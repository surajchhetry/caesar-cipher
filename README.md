# caesar-cipher
The Caesar Cipher is a simple **substitution cipher** where each letter in the plaintext is shifted by a fixed number of positions in the alphabet.

For example, with a shift of 3:

•	‘A’ → ‘D’

•	‘B’ → ‘E’

•	‘X’ → ‘A’ (wraps around)

•	‘Z’ → ‘C’

To decrypt, we shift in the opposite direction.

--- 

### How to implement ?

1. **Define the Alphabet**
   1. A **mapping rule** is needed that defines which characters will be replaced by which ones. In the Caesar Cipher, this mapping is created by shifting characters forward or backward **by a fixed position**.
   2. The standard Caesar Cipher works on **26 uppercase (A–Z)** and **26 lowercase (a–z)** letters.
   3. Numbers and special characters remain **unchanged** (unless we decide to include them).

2. **Shifting the Alphabet**
   
   1. Define **shift length ( shift key )** to determine how many positions each letter moves in the alphabet.
      
      
     ```
      Shift key : 3
      Plaintext:  ABCDEFGHIJKLMNOPQRSTUVWXYZ
      Shifted(3): DEFGHIJKLMNOPQRSTUVWXYZABC
     
     ```
   2. Define **Shift Direction**, example for **Encryption** , move letters forward in the alphabet by shift. For **Decryption**, move letters backward by shift

### Advantage

1. **Explicit Mapping** – We define an exact rule for shifting letters.
2. **Handles Upper & Lower Case Separately**: Preserves case sensitivity.
3. **Keeps Non-Alphabet Characters Unchanged** : Only shifts letters
4. **Reversible** : The same function works for encryption and decryption

### Disadvantage
1. **Easy to Break (Brute Force Attack)** :
   1. Only 25 Possible Shifts:
      - Since the English alphabet has 26 letters, an attacker can simply try all possible shifts (1 to 25) and find the correct one.
      - A computer can do this instantly, and even a human can manually decode it in a short time
        
  Example:
      If we encrypt "**HELLO**" with a shift of 3 , we get "**KHOOR**"
      An attacker can try all shifts and quickly recognize the correct word.

2. **Preserves Letter Frequency (Vulnerable to Frequency Analysis)**
    - Same letters always encrypt to the same letter
    - This means the most common letters (e.g., ‘E’ in English) remain the most common after encryption.
    - A frequency analysis attack can match letter distributions in the encrypted text to known English letter frequencies.
            
3. **No Key Variation (Fixed Shift)**
   - One fixed shift makes it predictable.
   - 	Once the shift is known, all messages encrypted with the same shift are compromised.
   - 	A stronger encryption method should allow different shifts per character (e.g., Vigenère Cipher, where shifts depend on a keyword).
  

### Mathematical Representation (Modular Arithmetic)

For a letter X in the alphabet:

Convert it to a numerical value (A = 0, B = 1, ..., Z = 25)
  
**Apply the shift**:

$E(x) = (x + s) \mod 26$

**where**:
   - *x*  is the position of the letter in the alphabet
   - *s*  is the shift key
   - *\mod 26*  ensures wrapping around from ‘Z’ back to ‘A’.
 
 **To decrypt, we reverse the shift**:

$D(x) = (x - s) \mod 26$


### Frequency Analysis: How to Crack the Cipher

Since Caesar Cipher preserves the relative frequency of letters, an attacker can analyze which letters appear most often and compare them to English letter frequency.

**Letter Frequency in English**

E T A O I N S H R D L C U M W F G Y P B V K J X Q Z

- E is the most common letter (~12.7%)
- T, A, O, I are also very frequent
- Q, X, Z are the rarest

By analyzing an encrypted text, we find the most common letter and assume it corresponds to ‘E’. From there, we calculate the shift and decrypt the message.

**Breaking Caesar Cipher with Frequency Analysis**

**Step 1: Count Letter Occurrences**
```text
Ciphertext:  KHOOR ZRUOG
Letter Frequency: O=2, R=2, K=1, H=1, Z=1, etc.
```

**Step 2: Identify the Most Frequent Letter**
  - Suppose ‘O’ is the most common letter in the ciphertext
  - If we assume ‘O’ represents ‘E’, then the shift is:
```Shift = Position of O - Position of ‘E = 14 - 4 = 10```
  

**Step 3: Decrypt Using the Found Shift**

Apply shift = -10 to get the original text.
  



   
