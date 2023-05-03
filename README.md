Download Link: https://assignmentchef.com/product/solved-cs2011-lab-1-manipulating-bits
<br>
The purpose of this assignment is to become more familiar with bit-level representations of integers and floating point numbers. You’ll do this by solving a series of programming “puzzles.” Many of these puzzles are quite artificial, but you’ll find yourself thinking much more about bits in working your way through them.

<h1>Logistics</h1>




This is an individual project. While this assignment has its own server at ⁀cs2011.cs.wpi.edu, final submission must be electronic via the Canvas system. In addition, see below for a ”Beat the Prof” contest.

Submissions to the contest and the assignment server <em>are not a substitute for </em>submissions via Canvas. Clar- ifications and corrections will be posted on the course Canvas site.







<h1>3        Handout Instructions</h1>




Start by creating a directory on your virtual machine to hold this assignment. Then download the file datalab-handout.tar from Canvas to this directory. Then give the command




unix&gt; tar xvf datalab-handout.tar




This will cause a number of files to be unpacked in the directory. The only file you will be modifying and turning in is bits.c.

Before you start: Insert <em>your name </em>and <em>your WPI username </em>in a comment at the top of the bits.c file. The penalty for failing to include your name on <em>any file of any submission </em>in this course is five points per file. It does not count to include your name and/or username as part of the name of a file or folder (although you may be required to <em>also </em>do this), because files can easily become detached from their names.




The bits.c file contains a skeleton for each of the 15 programming puzzles. Your assignment is to complete each function skeleton using only <em>straightline </em>code for the integer puzzles (i.e., no loops or con- ditionals) and a limited number of C arithmetic and logical operators. Specifically, you are <em>only </em>allowed to use the following eight operators:




! ˜ &amp; ˆ | + &lt;&lt; &gt;&gt;




A few of the functions further restrict this list, and some have fewer restrictions. Also, you are not allowed to use any constants longer than 8 bits. See the comments in bits.c for detailed rules and a discussion of the desired coding style.

Note: For this assignment, we will always use 32-bit numbers. Bits are numbered from the right, counting from zero. So, the rightmost (least-significant) bit is bit 0, and the leftmost is bit 31.







<h1>4        The Puzzles</h1>




This section describes the puzzles that you will be solving in bits.c.




<table>

 <tbody>

  <tr>

   <td width="293"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

4.1 Bit Manipulations




Table 1 describes a set of functions that manipulate and test sets of bits. The “Rating” field gives the difficulty rating (the number of points) for the puzzle, and the “Max ops” field gives the maximum number of operators you are allowed to use to implement each function. See the comments in bits.c for more details on the desired behavior of the functions. You may also refer to the test functions in tests.c. These are used as reference functions to express the correct behavior of your functions, although they don’t satisfy the coding rules for your functions.




Name                                   Description                                                                                Max Ops

oddBits(void) Return word with all odd-numbered bits set to 1 using    only !, ˜, &amp;, ˆ, |, +, &lt;&lt;, and &gt;&gt;.

isTmin(x) Returns 1 if x is the minimum, two’s complement  10 number, and 0 otherwise.

bitXor(x,y)        xˆy using only ˜ and &amp;.                                                               14

Same as x ? y : z.                                                                     16

greatestBitPos(x) Return a mask that marks the position of the most  70 significant 1 bit. If  x  ==  0, return 0.  greatestBitPos(96) = 0x40.




Table 1: Bit-Level Manipulation Functions.




4.2 Two’s Complement Arithmetic




Table 2 describes a set of functions that make use of the two’s complement representation of integers. Again, refer to the comments in bits.c and the reference versions in tests.c for more information.




Name Description Rating Max Ops divpwr2(x,n) Compute x/2<sup>n</sup> 2 15 isNonNegative(x) x &gt;= 0? 3 6

satMul2(x)     Multiplies by 2, saturating to Tmin or Tmax if over-        3          20            flow.

isLess(x, y) Return 1 if x &lt; y 3 24 isAsciiDigit(x) Return 1 if 0x30 &lt;= x &lt;= 0x39 (ASCII codes 3 15  for characters ’0’ to ’9’)

trueThreeFourths(x) Multiplies by 3/4, rounding toward 0. 4 20 ilog2(x) Compute ⌊ log<sub>2</sub>(x)⌋ 4 90




Table 2: Arithmetic Functions







4.3 Floating-Point Operations

<table>

 <tbody>

  <tr>

   <td width="293"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>




For this part of the assignment, you will implement some common single-precision floating-point opera- tions. In this section, you are allowed to use standard control structures (conditionals, loops), and you may use both int and unsigned data types, including arbitrary unsigned and integer constants. You may not use any unions, structs, or arrays. Most significantly, you may not use any floating point data types, operations, or constants. Instead, any floating-point operand will be passed to the function as having type unsigned, and any returned floating-point value will be of type unsigned. Your code should perform the bit manipulations that implement the specified floating point operations.

Table 3 describes a set of functions that operate on the bit-level representations of floating-point numbers. Refer to the comments in bits.c and the reference versions in tests.c for more information.




Name Description  Rating Max Ops float_neg(uf) Compute -f  2 10 float_i2f(x) Compute (float) x 4 30 float_twice(uf) Compute 2*f  4 30




Table 3: Floating-Point Functions. Value f is the floating-point number having the same bit representation as the unsigned integer uf.




Functions float_neg and float_twice must handle the full range of possible argument values, in- cluding not-a-number (NaN) and infinity. The IEEE standard does not specify precisely how to handle NaN’s, and the IA32 behavior is a bit obscure. We will follow a convention that for any function returning a NaN value, it will return the one with bit representation 0x7FC00000.




The included program fshow helps you understand the structure of floating point numbers. To compile fshow, switch to the handout directory and type:




unix&gt; make




You can use fshow to see what an arbitrary pattern represents as a floating-point number:




unix&gt; ./fshow 2080374784




Floating point value 2.658455992e+36

Bit Representation 0x7c000000, sign= 0, exponent= f8, fraction= 000000

Normalized. 1.0000000000 X 2ˆ(121)

You can also give fshow hexadecimal and floating point values, and it will decipher their bit structure.







<h1>5        Evaluation</h1>

Your score will be computed out of a maximum of 80 points based on the following distribution:




43 Correctness points.

<table>

 <tbody>

  <tr>

   <td width="293"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

30 Performance points.

7 Style points.




<em>Correctness points. </em>The 15 puzzles you must solve have been given a difficulty rating between 1 and 4, such that their weighted sum totals to 43. We will evaluate your functions using the btest program, which is described in the next section. You will get full credit for a puzzle if it passes all of the tests performed by btest, and no credit otherwise.

<em>Performance points. </em>Our main concern at this point in the course is that you can get the right answer. However, we want to instill in you a sense of keeping things as short and simple as you can. Furthermore, some of the puzzles can be solved by brute force, but we want you to be more clever. Thus, for each function we’ve established a maximum number of operators that you are allowed to use for each function. This limit is very generous and is designed only to catch egregiously inefficient solutions. You will receive two points for each correct function that satisfies the operator limit.

<em>Style points. </em>Finally, we’ve reserved 7 points for a subjective evaluation of the style of your solutions and your commenting. Your solutions should be as clean and straightforward as possible. Your comments should be informative, but they need not be extensive.







<h1>6        Autograding your work</h1>




We have included some autograding tools in the handout directory — btest, dlc, and driver.pl — to help you check the correctness of your work.




<ul>

 <li><strong>btest: </strong>This program checks the functional correctness of the functions in c. To build and use it, type the following two commands:</li>

</ul>




unix&gt; make unix&gt; ./btest

Notice that you must rebuild btest each time you modify your bits.c file.

You’ll find it helpful to work through the functions one at a time, testing each one as you go. You can use the -f flag to instruct btest to test only a single function:

unix&gt; ./btest -f bitAnd

You can feed it specific function arguments using the option flags -1, -2, and -3:

unix&gt; ./btest -f bitAnd -1 7 -2 0xf

Check the file README for documentation on running the btest program.

<ul>

 <li><strong>dlc</strong>: This is a modified version of an ANSI C compiler from the MIT CILK group that you can use to check for compliance with the coding rules for each puzzle. The typical usage is:</li>

</ul>




unix&gt; ./dlc bits.c

<table>

 <tbody>

  <tr>

   <td width="293"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

The program runs silently unless it detects a problem, such as an illegal operator, too many operators, or non-straightline code in the integer puzzles. Running with the -e switch:

unix&gt; ./dlc -e bits.c

causes dlc to print counts of the number of operators used by each function. Type ./dlc -help for a list of command line options.

<ul>

 <li><strong>pl</strong>: This is a driver program that uses btest and dlc to compute the correctness and performance points for your solution. It takes no arguments:</li>

</ul>




unix&gt; ./driver.pl

Your instructors will use driver.pl to evaluate your solution.