//# TwoPhaseMaxVowels
//O(n) Two-Phase Max Vowel Algorithm by //10th Grader


        
    class TwoPhaseMaxVowels {
    public static void main(String[] args) {
        String s = "Ram Nam Satya AA ei ou Hein".trim();
        // Phase 1: Extract first word as baseline
        String firstWord = "";
        int maxVowels = 0;
        for(int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if(ch != ' ') {
                firstWord += ch;
                if("aeiouAEIOU".indexOf(ch) != -1) maxVowels++;
            } else break;
        }
        
        String result = firstWord;
        // Phase 2: Compare remaining words
        int pos = s.indexOf(' ') + 1;
        String current = ""; int currentVowels = 0;
        for(int j = pos; j < s.length(); j++) {
            char ch = s.charAt(j);
            if(ch != ' ') {
                current += ch;
                if("aeiouAEIOU".indexOf(ch) != -1) currentVowels++;
            } else {
                if(currentVowels > maxVowels) {
                    maxVowels = currentVowels;
                    result = current;
                } else if(currentVowels == maxVowels) {
                    result += " " + current;
                }
                current = ""; currentVowels = 0;
            }
        }
        System.out.println(result);
    }
}    
