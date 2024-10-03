# Round-1
```
HATFD1005
Longest Palindromic Substring
Write a program to find the longest palindromic substring in a given string without using any built-in
substring or reverse functions. For example, for input "babad", the output should be "bab" or "aba".
Instructions:
Avoid using any string handling libraries. Implement a solution that checks all substrings manually
Solution:
#include <stdio.h>
#include <string.h>
int expandAroundCenter(char *s, int left, int right, int *start, int *maxLen) {
while (left >= 0 && right < strlen(s) && s[left] == s[right]) {
left--;
right++;
}
if (*maxLen < right - left - 1) {
*start = left + 1;
*maxLen = right - left - 1;
}
}
char* longestPalindrome(char *s) {
int start = 0, maxLen = 0;
for (int i = 0; i < strlen(s); i++) {
expandAroundCenter(s, i, i, &start, &maxLen);
expandAroundCenter(s, i, i + 1, &start, &maxLen);
}
static char result[1000];
for (int i = 0; i < maxLen; i++) {
result[i] = s[start + i];
}
result[maxLen] = '\0';
return result;
}
int main() {
char input[] = "babad";
printf("Longest Palindromic Substring: %s\n", longestPalindrome(input));
return 0;
}
```
![r1 ss](https://github.com/user-attachments/assets/867297e7-df34-4075-a707-f25d81a178b8)


