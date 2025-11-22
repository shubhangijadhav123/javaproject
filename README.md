import java.util.*;
 public class DNAAnalyzer {
    // Define 10 traits
    static String[] TRAITS = {
        "Eye Color", "Skin Color", "Hair Color", "Height", "Blood Group",
        "Behaviour", "Immunity", "Intelligence", "Body Type", "Voice Tone"
    };
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String[] father = new String[TRAITS.length];
        String[] mother = new String[TRAITS.length];
        System.out.println("DNA and Genetic Trait Analyzer");
        System.out.println("----------------------------------");
        System.out.println("Sample Input Section (Example):");
        System.out.println("----------------------------------");
        System.out.println("Eye Color: Brown / Blue");
        System.out.println("Skin Color: Fair / Medium / Dark");
        System.out.println("Hair Color: Black / Blonde / Brown");
        System.out.println("Height: Short / Medium / Tall");
        System.out.println("Blood Group: A+ / B+ / AB+ / O+");
        System.out.println("Behaviour: Calm / Cheerful / Aggressive");
        System.out.println("Immunity: Strong / Average / Weak");
        System.out.println("Intelligence: High / Moderate / Low");
        System.out.println("Body Type: Slim / Athletic / Fat");
        System.out.println("Voice Tone: Soft / Deep / Sharp");
        System.out.println("----------------------------------");
        System.out.println("Enter details for Father and Mother below:\n");
        // Taking user input
        for (int i = 0; i < TRAITS.length; i++) {
            System.out.print("Father's " + TRAITS[i] + ": ");
            father[i] = sc.nextLine().trim();
            System.out.print("Mother's " + TRAITS[i] + ": ");
            mother[i] = sc.nextLine().trim();
            System.out.println();
        }
        System.out.println("----------------------------------");
        System.out.println("Selected Input Section");
        System.out.println("----------------------------------");
        for (int i = 0; i < TRAITS.length; i++) {
            System.out.printf("%-15s -> Father: %-10s | Mother: %-10s%n",
                    TRAITS[i], father[i], mother[i]);
        }
        System.out.print("\nEnter number of children to simulate: ");
        int childCount = sc.nextInt();
        sc.nextLine(); // consume newline
        System.out.println("\nPredicting child traits...\n");
        Random rand = new Random();
        for (int c = 1; c <= childCount; c++) {
            System.out.println("Child " + c + " Prediction:\n");
            for (int i = 0; i < TRAITS.length; i++) {
                String trait = TRAITS[i];
                String f = father[i];
                String m = mother[i];
                String result;
                // Simple inheritance logic
                if (f.equalsIgnoreCase(m)) {
                    result = f;
                } else {
                    result = rand.nextDouble() < 0.5 ? f : m;
                }
                // Random influence percentage
                int chance = 50 + rand.nextInt(51); // between 50% and 100%
                System.out.printf("%-15s -> %-12s (Influence: %s, %d%%)%n",
                        trait, result, (result.equals(f) ? "Father" : "Mother"), chance);
            }
            System.out.println();
        }
        System.out.println("Analysis complete. Thank you!");
        sc.close();
    }
 }
