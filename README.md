# a-public-rest-api
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        // Simulated JSON response from a weather API
        String jsonResponse = "{ \"current_weather\": { \"temperature\": 22.5, \"windspeed\": 15.4, \"weathercode\": 3 } }";

        // Parse manually (since we can’t use org.json in online compilers)
        double temperature = extractDouble(jsonResponse, "temperature");
        double windspeed = extractDouble(jsonResponse, "windspeed");
        int weathercode = (int) extractDouble(jsonResponse, "weathercode");

        // Display structured weather info
        System.out.println("Current Weather (Simulated):");
        System.out.println("Temperature: " + temperature + " °C");
        System.out.println("Wind Speed: " + windspeed + " km/h");
        System.out.println("Weather Code: " + weathercode);
    }

    // Helper method to extract double values from a JSON-like string
    public static double extractDouble(String json, String key) {
        try {
            String pattern = "\"" + key + "\":";
            int start = json.indexOf(pattern) + pattern.length();
            int end = json.indexOf(",", start);
            if (end == -1) end = json.indexOf("}", start);
            return Double.parseDouble(json.substring(start, end).trim());
        } catch (Exception e) {
            return -1;
        }
    }
}
