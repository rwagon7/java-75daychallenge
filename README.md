# AlternatingString

! Key concepts for Alternating String ; to alternate we use step function or modulo function, minimize the scale with or function, 2 pointers, 1 pointer with max length bound while or for loop


## There are two ways to solve it in java ->
1) Let there be 2 words word1 & word2 with lengths m, n. We use a while loop with
  an expression (i < m || j < n) but eats up a lot of memory.

  below is the code ->


```java

  class Solution {
    public String mergeAlternately(String word1, String word2) {
        int m = word1.length();
        int n = word2.length();
        StringBuilder result = new StringBuilder();
        int i = 0, j = 0;

        while (i < m || j < n) {
            if (i < m) {
                result.append(word1.charAt(i++));
            }
            if (j < n) {
                result.append(word2.charAt(j++));
            }
        }

        return result.toString();
    }
}

```
2) Consider one pointer instead of two where we take maximumof the array & traverse through it.

  below is the code ->

```java

class Solution {
    public String mergeAlternately(String word1, String word2) {
        int m = word1.length();
        int n = word2.length();
        StringBuilder result = new StringBuilder();

        for (int i = 0; i < Math.max(m, n); i++) {
            if (i < m) {
                result.append(word1.charAt(i));
            }
            if (i < n) {
                result.append(word2.charAt(i));
            }
        }

        return result.toString();
    }
}

```

## GCD String

! key concepts for GCD String; adding string alternatively , mirror images , gcd , division , lcm , recursion

1) The Brute-Force Method

```java

class Solution {
    public boolean valid(String str1, String str2, int k) {
        int len1 = str1.length(), len2 = str2.length();
        if (len1 % k > 0 || len2 % k > 0) {
            return false;
        } else {
            String base = str1.substring(0, k);
            return str1.replace(base, "").isEmpty() && str2.replace(base, "").isEmpty();
        }
    }


    public String gcdOfStrings(String str1, String str2) {
        int len1 = str1.length(), len2 = str2.length();
        for (int i = Math.min(len1, len2); i >= 1; --i) {
            if (valid(str1, str2, i)) {
                return str1.substring(0, i);
            }
        }
        return "";
    }
}


```

2) The Greatest-Divisor Approach: In this approach we add both string in alternate order and equate them. If it does, we go to next step wher ewe calculate gcd between the length of 2 string using recursion.


```java

class Solution {
    public int gcd(int x, int y) {
        if (y == 0) {
            return x;
        } else {
            return gcd(y, x % y);
        }    
    }

    public String gcdOfStrings(String str1, String str2) {
        // Check if they have non-zero GCD string.
        if (!(str1 + str2).equals(str2 + str1)) {
            return "";
        }

        // Get the GCD of the two lengths.
        int gcdLength = gcd(str1.length(), str2.length());
        return str1.substring(0, gcdLength);
    }
}

```
