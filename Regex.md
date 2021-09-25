# Regex Tutorial (Regex Tutorial)

Lets understand what is Regex? And why it is important?

## What is Regex?

Regex (Regular Expression) contain a series of characters that define a pattern of text to be matched—to make a filter more specialized, or general. For example, the regular expression ^AL[.]* searches for all items beginning with AL. The filter condition EntityName Like ^..N[.]* filters for all devices which have an N as the third letter of their name, and EntityName Like [.]*G filters for all devices whose name ends with the letter G.

 
```
Example of checking email validation:
/[\w._%+-]+@[\w.-]+\.[a-zA-z]{2,4}/
```
* Regex can be used in may way : such as file search, Email search, or any type of search perform in web and on desktop uses Regex. We can also be used from the command line and within text-editors to find text within a file. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
- [Summary](#summary)

## Regex Components

### Anchors
Anchors are characters within the regular expression that allow the user to match strings that begin with or ends with (or both) certain characters. 

Examples of Anchors are as follows:

* `^Start` - matches any string that start with the anterior word
* `end$` - matches a string that end with preceeding word before the character
* `^Start end$` -    exact string match (starts and ends with The end)

* Examples:
```
^Hello          matches any string starting with `Hello`
World$          matches any string ending with `World`
^Hello World$   matches exact string
goodbye         matches any string that has the exact text `goodbye` in it
```

### Quantifiers
Qunatifiers are characters within the regular expression that specify how many instances a character, group, or character class must be represented in the input to be matched.

Examples of Quanitifers are as follows:

* `*` - matches a string that has the anterior followed by zero or more of the last character
* `+` - matches a string that has the anterior followed by one or more of the last character
* `?` - matches a string that has the atnerior follwoed by zero or one of the last character
* `{}` -  matches a string that has the anterior followed by how ever many the number in the brackets of the last character in the string
* `()*` - matches a string that has any anterior characters followed by zero or more copies of the string within the brackets
* Examples:
```
abc*        matches a string that has ab followed by zero or more c 
abc+        matches a string that has ab followed by one or more c
abc?        matches a string that has ab followed by zero or one c
abc{2}      matches a string that has ab followed by 2 c
abc{2,}     matches a string that has ab followed by 2 or more c
abc{2,5}    matches a string that has ab followed by 2 up to 5 c
a(bc)*      matches a string that has a followed by zero or more copies of the sequence bc
a(bc){2,5}  matches a string that has a followed by 2 up to 5 copies of the sequence bc
```

### OR operator
OR Operators (Alternation Operator) matches on of a choice of regular expressions: if you put the character(s) representing the alternation operator between any two characters in the regular expression, the result matches the union of the strings that those two characters match.

Examples of OR Operators are as follows:

* `(|)` - matches a string that has any anterior characters followed by the characters on the left or right of the vertical bar
* `[]` - matches a string that has any anterior characters without any characters within the brackets
* Examples: 
```
x(y|z)  matches a string that has x followed by y or z (and captures y or z)
x[yz]   matches a string that has x, but without capturing b or c
```

### Character classes
Character Classes (Character Set) tells the regex engine to match only one out serveral specific characters, such as digits, words, or whitespace

Examples of Character Classes are as follows:

* `\d` - matches a single character that is a digit
* `\w` - matches a word character (any alphanumeric character plus underscore)
* `\s` - matches a whitespace character (including tabs and line brakes)
* `.` - matches any character
* the capital case for any aformentioned characters will inverse the match
* Examples:
```
\d    matches a single any digit 0-9
\w    matches a single any character that is a-z
\s    matches ` `
.     matches any character
\D    matches a single non-digit character
\W    matches a single any non-character that is a-z
\S    matches a single non-` `
```

### Flags
Flags are optional parameters that we can add to a plain expression to make it search in a different way. Each flag is denoted by a single alphabetic character, and serves different purposes in modifying the expression's searching behavior.

Examples of Flags are as follows:
* `g` - Global, does not return after the first match, which restarted any subsequest searches from the end of the previous match (Makes the expression search for all occurences)
* `m` - Multi-line, when enabled the Anchors (^ $) will match the start and end of a line, rather than the whole string
* `i` - Insensitive, makes the entire expression case-insensitive
* Examples:
```
/Hello/g   matches all `Hello` in the test
/Hello/m   matches the beginning and ending of each line with `Hello`, rather than the whole string `Hello` itself
/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)
```

### Grouping and capturing
Grouping unifies a pattern or string so that it is matched in a complete block

Examples of Grouping are as follows:
* `()` - parentheses creates a capture group
* `(?:)` - using `?:` disables the capturing group
* `(?<>)` - using `?<>` puts a name to the group
* Examples:
```
a(bc)           parentheses create a capturing group with value bc 
a(?:bc)*        using ?: we disable the capturing group 
a(?<foo>bc)     using ?<foo> we put a name to the group 
```

### Bracket expressions
Bracket Expressions are characters enclosed by a bracket `[]` matching any single character within the brackets. 
*note: if the first character within the brackets is a `^` then it signifies any chracter **not** in the list, and is unspecified whether it matches an encoding error. 

Examples of Bracket Expressions are as follows: 
* `[]` - matching any single character within the brackets
* `[]%` - matching the string inside the brackets before the `%`
* `[^]` - matching any string that has not a letter from within the brackets (negation of expression)
* Examples:
```
[abc]            matches a string that has either an a or a b or a c -> is the same as a|b|c 
[a-c]            same as previous
[a-fA-F0-9]      a string that represents a single hexadecimal digit, case insensitively 
[0-9]%           a string that has a character from 0 to 9 before a % sign
[^a-zA-Z]        a string that has not a letter from a to z or from A to Z. In this case the ^ is used as negation of the expression 
```

### Greedy and Lazy Match
Greedy and/or Lazy Matching are quantifies that expand the match as far as possible through the text. 

Examples of Greedy and/or Lazy Matching are as follows:
* `* + {}` - any one of these character can be used as a quanitifer for a Greedy or Lazy Match
* Examples:
```
<.+?>     matches any character that is one or more times included inside `<` and `>`, and expands as needed.
<[^<>]+>  matches any character expects `<` or `>` one or more times included inside `<` and `>`. 
```

### Boundaries
Not to be confused with actual characters, simply put, Boundaries are the places between characters. A Boundary should be thought of as a wall between any adjacent characters.
There are two types of Boundaries, **Word** and ***Non-Word**, each denoted by a specific character. 

Examples of Boundaries are as follows:
* `\b` - A position that bounds a word, or where a word starts or ends. It denotes a place between a word and non-word character, at the start and end of a string.
* `\B` - Exact opposite of a word boundary, the negation of `\b` and will match **any position a word boundary doesnt.** *
* `*`Will match between a word and word character, as well as between a non-word and non-word character.
* Examples of Boundaries are as follows:
```
`Hello World` has 12 total Boundaries with 8 Word Boundaries as seen below:
|H|e|l|l|o| |W|o|r|l|d|
^ ^ ^ ^ ^ ^ ^ ^ ^ ^ ^ ^
N W W W W N N W W W W N  -  N = Nonword Boundary \ W = Word Boundary
\bxyz\b     matches a "whole words only search" for the string `xyz`
\Bxyz\B     matches only if the pattern is fully surrounded by word characters `txyzt` would match the string `xyz` because it only has word boundaries
```

### Back-references
When using Grouping (look above) you may Capture the Group, which is saved in memory for later use. Backreferencing is the name given to the action of using these matches. 
Backreferencing is the refernce of a captured match, save in memory, by a captured group.

Examples are a follows:
```
([xyz])\1              using \1 it matches the same text that was matched by the first capturing group
([uwx])([yz])\2\1      we can use \2 (\3, \4, etc.) to identify the same text that was matched by the second (third, fourth, etc.) capturing group
(?<bar>[xzy])\k<bar>   we put the name bar to the group and we reference it later (\k<foo>). The result is the same of the first regex
```
### Look-ahead and Look-behind
Look-ahead and Look-behind (lookaround) are `start and end` zero-length assertions [Anchors](#anchors) but they actually match characters, then ends the match, returning only the result: **Match or No Match**. They do not cosume characters in the string, but only assert wether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.

Examples of Look-ahead and Look-behind are as follows:
```
h(?=t)       matches a h only if is followed by t, but t will not be part of the match
(?<=t)h      matches a h only if is preceded by an t, but t will not be part of the match

NEGATION OPERATOR

h(?!t)       matches a h only if is not followed by t, but t will not be part of the match
(?<!t)h      matches a h only if is not preceded by an t, but t will not be part of the match

```

### Summary
As you’ve seen, the application fields of regex can be multiple and I’m sure that you’ve  come across at least one of these tasks among those seen in your developer career, here a quick list:

* data validation (for example check if a email address is in valid format or not)
* data scraping (especially web scraping, find all pages that contain a certain set of words eventually in a specific order)
* data wrangling (transform data from “raw” to another format)
* string parsing (for example catch all URL GET parameters, capture text inside a set of parenthesis)
* string replacement (for example, even during a code session using a common IDE to translate a Java or C# class in the respective JSON object — replace “;” with “,” make it lowercase, avoid type declaration, etc.)
* syntax highlightning, file renaming, packet sniffing and many other applications involving strings (where data need not be textual)