# Ex-2-GENERATION OF LEXICAL TOKENS LEX FLEX TOOL
# Reg.No:212223040240
# Date:15/04/25
# AIM
## To write a lex program to implement lexical analyzer to recognize a few patterns.
# ALGORITHM

1.	Start the program.

2.	Lex program consists of three parts.

     a.	Declaration %%

     b.	Translation rules %%

     c.	Auxilary procedure.

3.	The declaration section includes declaration of variables, maintest, constants and regular definitions.
4.	Translation rule of lex program are statements of the form

    a.	P1 {action}

    b.	P2 {action}

    c.	…

    d.	…

    e.	Pn {action}

5.	Write a program in the vi editor and save it with .l extension.

6.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l $ cc lex.yy.c
7.	Compile that file with C compiler and verify the output.

# INPUT
```
%{
#include <stdio.h>
#include <string.h>

int isKeyword(const char *str) {
    const char *keywords[] = {"if", "else", "while", "for", "int"};
    for (int i = 0; i < 5; ++i) {
        if (strcmp(str, keywords[i]) == 0)
            return 1;
    }
    return 0;
}
%}

%%

[ \t\n]+              ; // Ignore whitespace
"+"|"-"|"*"|"/"|"="   { printf("Operator: %s\n", yytext); }
[0-9]+                { printf("Number: %s\n", yytext); }
[a-zA-Z_][a-zA-Z0-9_]* {
                        if (isKeyword(yytext)) {
                            printf("Keyword: %s\n", yytext);
                        } else {
                            printf("Identifier: %s\n", yytext);
                        }
                    }

.                     ; // Ignore other characters

%%

int main(void) {
    printf("Enter your input: ");
    yylex();
    return 0;
}

int yywrap(void) {
    return 1;
}
```
# OUTPUT
![Screenshot 2025-04-15 115553](https://github.com/user-attachments/assets/9e93a5ef-3a74-48bd-bfcb-4aa2144f03ba)

# RESULT
 The lexical analyzer is implemented using lex and the output is verified.
