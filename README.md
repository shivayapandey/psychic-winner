 # psychic-
run lex file

vi filename.lex
lex filename.lex
cc lex.yy.c -lfl
./a.out



pos_neg.lex

%{
#include <stdio.h>
%}

%%
[+-]?[0-9]+     { printf("%s is ", yytext);
                  int num = atoi(yytext);
                  if (num > 0)
                      printf("positive\n");
                  else if (num < 0)
                      printf("negative\n");
                  else
                      printf("neither positive nor negative\n");
                }
.|\n            ;

%%
int yywrap(){}

int main() {
    yylex();
    return 0;
}




odd_eve.lex

%{
#include <stdio.h>
%}

%%
[0-9]+          { printf("%s is ", yytext);
                  int num = atoi(yytext);
                  if (num % 2 == 0)
                      printf("even\n");
                  else
                      printf("odd\n");
                }
.|\n            ;

%%
int yywrap(){}
int main() {
    yylex();
    return 0;
}






    
prime.lex

%{
/* Definition section */
#include<stdio.h>
#include<stdlib.h>
int flag,c,j;
%}

/* Rule Section */
%%
[0-9]+ {c=atoi(yytext);
                if(c==2)
                {
                printf("Prime number\n");
                }
                else if(c==0 || c==1)
                {
                printf("Not a Prime number\n");
                }
                else
                {
                for(j=2;j<c;j++)
                {
                if(c%j==0)
                flag=1;
                }
                if(flag==1)
                printf("Not a prime number\n");
                else if(flag==0)
                printf("Prime number\n");
                }
        }
%%
int yywrap(){}
// driver code
int main()
 { 
  yylex(); 
  return 0; 
 } 




no_of_words.lex

/*lex program to count number of words*/
%{
#include<stdio.h>
#include<string.h>
int i = 0;
%}

/* Rules Section*/
%%
([a-zA-Z0-9])* {i++;} /* Rule for counting
                                                number of words*/

"\n" {printf("%d\n", i); i = 0;}
%%

int yywrap(){}

int main()
{
        // The function that starts the analysis
        yylex();

        return 0;
}





lexical analyser

lexcode.lex
%{
int COMMENT=0;
%}

identifier [a-zA-Z][a-zA-Z0-9]*

%%
#.* {printf("\n%s is a preprocessor directive",yytext);}
int |
float |
char |
double |
while |
for |
struct |
typedef |
do |
if |
break |
continue |
void |
switch |
return |
else |
goto {printf("\n\t%s is a keyword",yytext);}
"\/\*" {COMMENT=1; printf("\n\t%s is a COMMENT",yytext);}
{identifier}\( {if(!COMMENT)printf("\nFUNCTION \n\t%s",yytext);}
\{  {if(!COMMENT)printf("\n BLOCK BEGINS");}
\}  {if(!COMMENT)printf("BLOCK ENDS ");}
{identifier}(\[[0-9]*\])? {if(!COMMENT) printf("\n %s IDENTIFIER",yytext);}
\".*\" {if(!COMMENT)printf("\n\t %s is a STRING",yytext);}
[0-9]+ {if(!COMMENT) printf("\n %s is a NUMBER ",yytext);}
\)(\:)? {if(!COMMENT)printf("\n\t");ECHO;printf("\n");}
\( ECHO;
= {if(!COMMENT)printf("\n\t %s is an ASSIGNMENT OPERATOR",yytext);}
\<= |
\>= |
\< |
== |
\> {if(!COMMENT) printf("\n\t%s is a RELATIONAL OPERATOR",yytext);}
%%

int main(int argc, char **argv)
{
    FILE *file;
    file=fopen("var.c","r");
    if(!file)
    {
        printf("could not open the file");
        exit(0);
    }
    yyin=file;
    yylex();
    printf("\n");
    return(0);
}

int yywrap()
{
    return(1);
}



var.c
#include<stdio.h>
#include<conio.h>
void main()
{
int a,b,c;
a=1;
b=2;
c=a+b;
printf("Sum:%d",c);
}




#include<stdio.h> is a preprocessor directive

#include<conio.h> is a preprocessor directive

        void is a keyword
FUNCTION
        main(
        )


 BLOCK BEGINS

        int is a keyword
 a IDENTIFIER,
 b IDENTIFIER,
 c IDENTIFIER;

 a IDENTIFIER
         = is an ASSIGNMENT OPERATOR
 1 is a NUMBER ;

 b IDENTIFIER
         = is an ASSIGNMENT OPERATOR
 2 is a NUMBER ;

 c IDENTIFIER
         = is an ASSIGNMENT OPERATOR
 a IDENTIFIER+
 b IDENTIFIER;

FUNCTION
        printf(
         "Sum:%d" is a STRING,
 c IDENTIFIER
        )
;
BLOCK ENDS









java to identify odd or even
import java.util.Scanner;

public class EvenOdd {

    public static void main(String[] args) {

        Scanner reader = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = reader.nextInt();

        if(num % 2 == 0)
            System.out.println(num + " is even");
        else
            System.out.println(num + " is odd");
    }
}





perimeter of rectangle
import java.util.Scanner;

public class RectanglePerimeter {
   public static void main(String args[]) {
      float a ,b, perimeter;
      System.out.println("Required packages have been imported");
      Scanner my_scanner = new Scanner(System.in);
      System.out.println("A Scanner object has been defined ");
      System.out.print("Enter the length of first side : ");
      a = my_scanner.nextFloat();
      System.out.print("Enter the length of second side : ");
      b = my_scanner.nextFloat();
      
     
      perimeter = 2*(a + b);
      System.out.printf("\nThe perimeter of Rectangle is: %.2f", perimeter);
   }
}





factorial of a number
import java.util.Scanner;
public class Factorial {

    public static void main(String[] args) {
        Scanner my=new Scanner(System.in);
        int num ;
        num=my.nextInt();
        long factorial = 1;
        for(int i = 1; i <= num; ++i)
        {
            // factorial = factorial * i;
            factorial *= i;
        }
        System.out.printf("Factorial of %d = %d", num, factorial);
    }
}





vowel or consonent

import java.util.Scanner;

public class VowelConsonant {

    public static void main(String[] args) {
        Scanner my = new Scanner(System.in);
        
        System.out.print("Enter a character: ");
        char ch = my.next().charAt(0);

        if(ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' ||
           ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U' )
            System.out.println(ch + " is a vowel");
        else
            System.out.println(ch + " is a consonant");
    }
}




biggest of 3 nos
import java.util.Scanner;
public class Biggest_Number 
{
    public static void main(String[] args) 
    {
        int x, y, z;
        Scanner s = new Scanner(System.in);
        System.out.print("Enter the first number: ");
        x = s.nextInt();
        System.out.print("Enter the second number: ");
        y = s.nextInt();
        System.out.print("Enter the third number: ");
        z = s.nextInt();
        if ( x > y )
        {
            if ( x > z )
            {
                System.out.println("Largest number: " + x);
            }
            else
            {
                System.out.println("Largest number: " + z);
            }
        }
        else
        {
            if ( y > z )
            {
                System.out.println("Largest number: " + y);
            }
            else 
            {
                System.out.println("Largest number: " + z);
            }
        }
    }
}






max of n arrays
// Java Program to find maximum in arr[] 

// Driver Class
class Test 
{ 
	// array declared
	static int arr[] = {10, 324, 45, 90, 9808}; 
	
	// Method to find maximum in arr[] 
	static int largest() 
	{ 
		int i; 
		
		// Initialize maximum element 
		int max = arr[0]; 
		
		// Traverse array elements from second and 
		// compare every element with current max 
		for (i = 1; i < arr.length; i++) 
			if (arr[i] > max) 
				max = arr[i]; 
		
		return max; 
	} 
	
	// Driver method 
	public static void main(String[] args) 
	{ 
		System.out.println("Largest in given array is " + largest()); 
	} 
} 









Bison calculator


calc.yacc

%{
#include<stdio.h>

int regs[26];
int base;

%}

%start list

%union { int a; }


%token DIGIT LETTER

%left '|'
%left '&'
%left '+' '-'
%left '*' '/' '%'
%left UMINUS  /*supplies precedence for unary minus */

%%                   /* beginning of rules section */

list:                       /*empty */
         |
        list stat '\n'
         |
        list error '\n'
         {
           yyerrok;
         }
         ;
stat:    expr
         {
           printf("%d\n",$1);
         }
         |
         LETTER '=' expr
         {
           regs[$1.a] = $3.a;
         }

         ;

expr:    '(' expr ')'
         {
           $$ = $2;
         }
         |
         expr '*' expr
         {

           $$.a = $1.a * $3.a;
         }
         |
         expr '/' expr
         {
           $$.a = $1.a / $3.a;
         }
         |
         expr '%' expr
         {
           $$.a = $1.a % $3.a;
         }
         |
         expr '+' expr
         {
           $$.a = $1.a + $3.a;
         }
         |
         expr '-' expr
         {
           $$.a = $1.a - $3.a;
         }
         |
         expr '&' expr
         {
           $$.a = $1.a & $3.a;
         }
         |
         expr '|' expr
         {
           $$.a = $1.a | $3.a;
         }
         |

        '-' expr %prec UMINUS
         {
           $$.a = -$2.a;
         }
         |
         LETTER
         {
           $$.a = regs[$1.a];
         }

         |
         number
         ;

number:  DIGIT
         {
           $$ = $1;
           base = ($1.a==0) ? 8 : 10;
         }       |
         number DIGIT
         {
           $$.a = base * $1.a + $2.a;
         }
         ;

%%
main()
{
 return(yyparse());
}

yyerror(s)
char *s;
{
  fprintf(stderr, "%s\n",s);
}

yywrap()
{
  return(1);
}




calc.lex
%{

#include <stdio.h>
#include "y.tab.h"
int c;
%}
%%
" "       ;
[a-z]     {
            c = yytext[0];
            yylval.a = c - 'a';
            return(LETTER);
          }
[0-9]     {
            c = yytext[0];
            yylval.a = c - '0';
            return(DIGIT);
          }
[^a-z0-9\b]    {
                 c = yytext[0];
                 return(c);
              }
%%


yacc -d calc.yacc
lex calc.lex
cc y.tab.c lex.yy.c
./a.out







pred_pars.c
#include <stdio.h>
#include <string.h>
 
char prol[7][10] = { "S", "A", "A", "B", "B", "C", "C" };
char pror[7][10] = { "A", "Bb", "Cd", "aB", "@", "Cc", "@" };
char prod[7][10] = { "S->A", "A->Bb", "A->Cd", "B->aB", "B->@", "C->Cc", "C->@" };
char first[7][10] = { "abcd", "ab", "cd", "a@", "@", "c@", "@" };
char follow[7][10] = { "$", "$", "$", "a$", "b$", "c$", "d$" };
char table[5][6][10];
 
int numr(char c)
{
   switch (c)
   {
      case 'S':
         return 0;
 
      case 'A':
         return 1;
 
      case 'B':
         return 2;
 
      case 'C':
         return 3;
 
      case 'a':
         return 0;
 
      case 'b':
         return 1;
 
      case 'c':
         return 2;
 
      case 'd':
         return 3;
 
      case '$':
         return 4;
   }
 
   return (2);
}
 
int main()
{
   int i, j, k;
 
   for (i = 0; i < 5; i++)
      for (j = 0; j < 6; j++)
         strcpy(table[i][j], " ");
 
   printf("The following grammar is used for Parsing Table:\n");
 
   for (i = 0; i < 7; i++)
      printf("%s\n", prod[i]);
 
   printf("\nPredictive parsing table:\n");
 
   fflush(stdin);
 
   for (i = 0; i < 7; i++)
   {
      k = strlen(first[i]);
      for (j = 0; j < 10; j++)
         if (first[i][j] != '@')
            strcpy(table[numr(prol[i][0]) + 1][numr(first[i][j]) + 1], prod[i]);
   }
 
   for (i = 0; i < 7; i++)
   {
      if (strlen(pror[i]) == 1)
      {
         if (pror[i][0] == '@')
         {
            k = strlen(follow[i]);
            for (j = 0; j < k; j++)
               strcpy(table[numr(prol[i][0]) + 1][numr(follow[i][j]) + 1], prod[i]);
         }
      }
   }
 
   strcpy(table[0][0], " ");
 
   strcpy(table[0][1], "a");
 
   strcpy(table[0][2], "b");
 
   strcpy(table[0][3], "c");
 
   strcpy(table[0][4], "d");
 
   strcpy(table[0][5], "$");
 
   strcpy(table[1][0], "S");
 
   strcpy(table[2][0], "A");
 
   strcpy(table[3][0], "B");
 
   strcpy(table[4][0], "C");
 
   printf("\n--------------------------------------------------------\n");
 
   for (i = 0; i < 5; i++)
      for (j = 0; j < 6; j++)
      {
         printf("%-10s", table[i][j]);
         if (j == 5)
            printf("\n--------------------------------------------------------\n");
      }
}






first and follow



first.c
// C program to calculate the First and
// Follow sets of a given grammar
#include <ctype.h>
#include <stdio.h>
#include <string.h>

// Functions to calculate Follow
void followfirst(char, int, int);
void follow(char c);

// Function to calculate First
void findfirst(char, int, int);

int count, n = 0;

// Stores the final result
// of the First Sets
char calc_first[10][100];

// Stores the final result
// of the Follow Sets
char calc_follow[10][100];
int m = 0;

// Stores the production rules
char production[10][10];
char f[10], first[10];
int k;
char ck;
int e;

int main(int argc, char** argv)
{
	int jm = 0;
	int km = 0;
	int i, choice;
	char c, ch;
	count = 8;

	// The Input grammar
	strcpy(production[0], "X=TnS");
	strcpy(production[1], "X=Rm");
	strcpy(production[2], "T=q");
	strcpy(production[3], "T=#");
	strcpy(production[4], "S=p");
	strcpy(production[5], "S=#");
	strcpy(production[6], "R=om");
	strcpy(production[7], "R=ST");

	int kay;
	char done[count];
	int ptr = -1;

	// Initializing the calc_first array
	for (k = 0; k < count; k++) {
		for (kay = 0; kay < 100; kay++) {
			calc_first[k][kay] = '!';
		}
	}
	int point1 = 0, point2, xxx;

	for (k = 0; k < count; k++) {
		c = production[k][0];
		point2 = 0;
		xxx = 0;

		// Checking if First of c has
		// already been calculated
		for (kay = 0; kay <= ptr; kay++)
			if (c == done[kay])
				xxx = 1;

		if (xxx == 1)
			continue;

		// Function call
		findfirst(c, 0, 0);
		ptr += 1;

		// Adding c to the calculated list
		done[ptr] = c;
		printf("\n First(%c) = { ", c);
		calc_first[point1][point2++] = c;

		// Printing the First Sets of the grammar
		for (i = 0 + jm; i < n; i++) {
			int lark = 0, chk = 0;

			for (lark = 0; lark < point2; lark++) {

				if (first[i] == calc_first[point1][lark]) {
					chk = 1;
					break;
				}
			}
			if (chk == 0) {
				printf("%c, ", first[i]);
				calc_first[point1][point2++] = first[i];
			}
		}
		printf("}\n");
		jm = n;
		point1++;
	}
	printf("\n");
	printf("-----------------------------------------------"
		"\n\n");
	char donee[count];
	ptr = -1;

	// Initializing the calc_follow array
	for (k = 0; k < count; k++) {
		for (kay = 0; kay < 100; kay++) {
			calc_follow[k][kay] = '!';
		}
	}
	point1 = 0;
	int land = 0;
	for (e = 0; e < count; e++) {
		ck = production[e][0];
		point2 = 0;
		xxx = 0;

		// Checking if Follow of ck
		// has already been calculated
		for (kay = 0; kay <= ptr; kay++)
			if (ck == donee[kay])
				xxx = 1;

		if (xxx == 1)
			continue;
		land += 1;

		// Function call
		follow(ck);
		ptr += 1;

		// Adding ck to the calculated list
		donee[ptr] = ck;
		printf(" Follow(%c) = { ", ck);
		calc_follow[point1][point2++] = ck;

		// Printing the Follow Sets of the grammar
		for (i = 0 + km; i < m; i++) {
			int lark = 0, chk = 0;
			for (lark = 0; lark < point2; lark++) {
				if (f[i] == calc_follow[point1][lark]) {
					chk = 1;
					break;
				}
			}
			if (chk == 0) {
				printf("%c, ", f[i]);
				calc_follow[point1][point2++] = f[i];
			}
		}
		printf(" }\n\n");
		km = m;
		point1++;
	}
}

void follow(char c)
{
	int i, j;

	// Adding "$" to the follow
	// set of the start symbol
	if (production[0][0] == c) {
		f[m++] = '$';
	}
	for (i = 0; i < 10; i++) {
		for (j = 2; j < 10; j++) {
			if (production[i][j] == c) {
				if (production[i][j + 1] != '\0') {
					// Calculate the first of the next
					// Non-Terminal in the production
					followfirst(production[i][j + 1], i,
								(j + 2));
				}

				if (production[i][j + 1] == '\0'
					&& c != production[i][0]) {
					// Calculate the follow of the
					// Non-Terminal in the L.H.S. of the
					// production
					follow(production[i][0]);
				}
			}
		}
	}
}

void findfirst(char c, int q1, int q2)
{
	int j;

	// The case where we
	// encounter a Terminal
	if (!(isupper(c))) {
		first[n++] = c;
	}
	for (j = 0; j < count; j++) {
		if (production[j][0] == c) {
			if (production[j][2] == '#') {
				if (production[q1][q2] == '\0')
					first[n++] = '#';
				else if (production[q1][q2] != '\0'
						&& (q1 != 0 || q2 != 0)) {
					// Recursion to calculate First of New
					// Non-Terminal we encounter after
					// epsilon
					findfirst(production[q1][q2], q1,
							(q2 + 1));
				}
				else
					first[n++] = '#';
			}
			else if (!isupper(production[j][2])) {
				first[n++] = production[j][2];
			}
			else {
				// Recursion to calculate First of
				// New Non-Terminal we encounter
				// at the beginning
				findfirst(production[j][2], j, 3);
			}
		}
	}
}

void followfirst(char c, int c1, int c2)
{
	int k;

	// The case where we encounter
	// a Terminal
	if (!(isupper(c)))
		f[m++] = c;
	else {
		int i = 0, j = 1;
		for (i = 0; i < count; i++) {
			if (calc_first[i][0] == c)
				break;
		}

		// Including the First set of the
		// Non-Terminal in the Follow of
		// the original query
		while (calc_first[i][j] != '!') {
			if (calc_first[i][j] != '#') {
				f[m++] = calc_first[i][j];
			}
			else {
				if (production[c1][c2] == '\0') {
					// Case where we reach the
					// end of a production
					follow(production[c1][0]);
				}
				else {
					// Recursion to the next symbol
					// in case we encounter a "#"
					followfirst(production[c1][c2], c1,
								c2 + 1);
				}
			}
			j++;
		}
	}
}








operator precedence
oper_prec.c
#include <stdio.h>

int main() {
    char stack[20], ip[20], opt[10][10][2], ter[10];
    int i, j, k, n, top = 0, col, row;

    printf("Enter the number of terminals: ");
    scanf("%d", &n);

    printf("Enter the terminals: ");
    scanf("%s", ter);

    printf("Enter the table values:\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < n; j++) {
            printf("Enter the value for %c %c: ", ter[i], ter[j]);
            scanf("%s", opt[i][j]);
        }
    }

    printf("\nOPERATOR PRECEDENCE TABLE:\n");
    printf("\t");
    for (i = 0; i < n; i++) {
        printf("%c\t", ter[i]);
    }
    printf("\n");
    for (i = 0; i < n; i++) {
        printf("%c\t", ter[i]);
        for (j = 0; j < n; j++) {
            printf("%c\t", opt[i][j][0]);
        }
        printf("\n");
    }

    stack[top] = '$';
    printf("\nEnter the input string: ");
    scanf("%s", ip);

    i = 0;
    printf("\nSTACK\t\tINPUT STRING\t\tACTION\n");
    printf("%s\t\t%s\t\t", stack, ip);

    while (i <= strlen(ip)) {
        for (k = 0; k < n; k++) {
            if (stack[top] == ter[k]) col = k;
            if (ip[i] == ter[k]) row = k;
        }

        if ((stack[top] == '$') && (ip[i] == '$')) {
            printf("String is accepted\n");
            break;
        } else if ((opt[col][row][0] == '<') || (opt[col][row][0] == '=')) {
            stack[++top] = opt[col][row][0];
            stack[++top] = ip[i];
            printf("Shift %c\n", ip[i]);
            i++;
        } else {
            if (opt[col][row][0] == '>') {
                while (stack[top] != '<') --top;
                top = top - 1;
                printf("Reduce\n");
            } else {
                printf("\nString is not accepted\n");
                break;
            }
        }

        printf("\n");
        for (k = 0; k <= top; k++) {
            printf("%c", stack[k]);
        }
        printf("\t\t\t");

        for (k = i; k < strlen(ip); k++) {
            printf("%c", ip[k]);
        }
        printf("\t\t\t");
    }

    return 0;
}



root@lipikasoni:~# ./a.out
Enter the number of terminals: 4
Enter the terminals: +*i$
Enter the table values:
Enter the value for + +: >
Enter the value for + *: <
Enter the value for + i: <
Enter the value for + $: >
Enter the value for * +: >
Enter the value for * *: >
Enter the value for * i: <
Enter the value for * $: >
Enter the value for i +: >
Enter the value for i *: >
Enter the value for i i: =
Enter the value for i $: >
Enter the value for $ +: <
Enter the value for $ *: <
Enter the value for $ i: <
Enter the value for $ $: A

OPERATOR PRECEDENCE TABLE:
        +       *       i       $
+       >       <       <       >
*       >       >       <       >
i       >       >       =       >
$       <       <       <       A

Enter the input string: i+i*i$

STACK           INPUT STRING            ACTION
$               i+i*i$          Shift i

$<i                     +i*i$                   Reduce

$                       +i*i$                   Shift +

$<+                     i*i$                    Shift i

$<+<i                   *i$                     Reduce

$<+                     *i$                     Shift *

$<+<*                   i$                      Shift i

$<+<*<i                 $                       Reduce

$<+<*                   $                       Reduce

$<+                     $                       Reduce

$                       $                       String is accepted
root@lipikasoni:~# vi oper_prec.c





infix to postfix
inf_to_post.c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Function to return precedence of operators
int prec(char c) {
	if (c == '^')
		return 3;
	else if (c == '/' || c == '*')
		return 2;
	else if (c == '+' || c == '-')
		return 1;
	else
		return -1;
}

// Function to return associativity of operators
char associativity(char c) {
	if (c == '^')
		return 'R';
	return 'L'; // Default to left-associative
}

// The main function to convert infix expression to postfix expression
void infixToPostfix(char s[]) {
	char result[1000];
	int resultIndex = 0;
	int len = strlen(s);
	char stack[1000];
	int stackIndex = -1;

	for (int i = 0; i < len; i++) {
		char c = s[i];

		// If the scanned character is an operand, add it to the output string.
		if ((c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z') || (c >= '0' && c <= '9')) {
			result[resultIndex++] = c;
		}
		// If the scanned character is an ‘(‘, push it to the stack.
		else if (c == '(') {
			stack[++stackIndex] = c;
		}
		// If the scanned character is an ‘)’, pop and add to the output string from the stack
		// until an ‘(‘ is encountered.
		else if (c == ')') {
			while (stackIndex >= 0 && stack[stackIndex] != '(') {
				result[resultIndex++] = stack[stackIndex--];
			}
			stackIndex--; // Pop '('
		}
		// If an operator is scanned
		else {
			while (stackIndex >= 0 && (prec(s[i]) < prec(stack[stackIndex]) ||
									prec(s[i]) == prec(stack[stackIndex]) &&
										associativity(s[i]) == 'L')) {
				result[resultIndex++] = stack[stackIndex--];
			}
			stack[++stackIndex] = c;
		}
	}

	// Pop all the remaining elements from the stack
	while (stackIndex >= 0) {
		result[resultIndex++] = stack[stackIndex--];
	}

	result[resultIndex] = '\0';
	printf("%s\n", result);
}

// Driver code
int main() {
	char exp[] = "a+b*(c^d-e)^(f+g*h)-i";

	// Function call
	infixToPostfix(exp);

	return 0;
}








