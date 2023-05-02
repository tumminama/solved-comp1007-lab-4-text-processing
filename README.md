Download Link: https://assignmentchef.com/product/solved-comp1007-lab-4-text-processing
<br>
Human languages are stored as texts in computers, such as articles, news, novels, speeches, etc. Text processing is an important step to analyze the meaning of sentences or documents. Python can be used to process the huge amount of text data for the requirements in various textual data analysis. This lab shows some very preliminary text processing functions in Python. For a more comprehensive treatment on the topic, refer to the online Python documentation at: <u>https://docs.python.org/3/library/stdtypes.html#textseq</u> and  <u>https://docs.python.org/3/library/text.html</u>

<h1>Background of        Text   Coding</h1>

Today’s digital computers represent everything by binary numbers, i.e., 0 and 1.  It’s important to have global standards on how to represent information (such as numbers, texts, images, audio, video, etc.) in computers so that different computers can exchange information without misunderstanding. Below are some fundamental terminologies related to digitalized information:

<strong>Bit</strong>: A single 0 or 1 is called a bit.

<strong>Byte</strong>: Eight bits form a byte. There are 256 different bytes, from 00000000 to 11111111.

<strong>Word</strong>: Several bytes form a word (e.g., we may have 2‐byte word, 4‐byte word, or 8‐byte word).

<h2>ASCII   Code</h2>

In 1968, the ASCII (American Standard Code for Information Interchange) code was standardized. ASCII defined numeric codes from 0 to 127 for various characters, including <strong><em>digits</em></strong> 0 to 9, <strong><em>lowercase letters</em></strong> a to z, <strong><em>uppercase letters</em></strong> A to Z, and some widely used <strong><em>punctuation symbols</em></strong>. In practice, an ASCII character occupies a single byte. Check out <u>https://en.wikipedia.org/wiki/ASCII</u> for the history and details of ASCII. However, ASCII code is designed for English characters only and cannot be used for other human languages.

<h2>Unicode</h2>

Unicode is a standard for the consistent encoding, representation, and handling of text expressed in most of the world’s writing systems. The Unicode standard describes how characters are represented by different integers called <strong>code points</strong>. To be compatible with the popular ASCII, the first 128 code points (i.e., integers 0 to 127) in Unicode are the same as ASCII code. The latest version Unicode 11.0 contains more than 1 million code points that covers 146 modern and historic scripts, organized as a set of tables for different languages. But how to represent a code point (i.e., an integer ranged from 0 to more than 1million) by 0s and 1s? There are different solutions known as <strong>character encodings</strong>, such as <strong><em>UTF‐8</em></strong>, <strong><em>UTF‐16</em></strong>, and <strong><em>UTF‐32</em></strong>. <strong><u>Python 3.x uses UTF‐8 as the default</u> <u>encoding to represent characters and strings</u></strong>.

<h2>UTF‐8</h2>

UTF‐8 is the dominant character encoding scheme of Unicode on the World Wide Web. It uses one byte for the first 128 code points (the same as ASCII), and <strong>up to</strong> 4 bytes for other characters. So any ASCII text is also a UTF‐8 text, which is a nice feature because a software developed for UTF‐8 can automatically process all existing ASCII‐based documents. Chinese, Japanese and Korean characters are encoded in 3 bytes in UTF‐8.

<strong>Summary</strong>: Unicode defines how to map a character to a code point (essentially an integer). Encoding schemes such as UTF‐8, UTF‐16, and UTF‐32 define how to represent a code point by one or a few bytes for storage or communication purposes. In order to correctly process a plain text document, a software needs to know the exact encoding scheme.

<h1>Strings</h1>

In Python, a <strong>string</strong> is an <strong>object</strong> that stores a sequence of characters. Strings have the built‐in data type <strong>str</strong> with many handy features. Notice that Python has no specific data type for characters (<strong>chars</strong>). A character is simply a string with length of 1. String literals can be enclosed by single, double or triple quotes, such as “Alice”, ‘Bob’, etc. Python strings are <strong>immutable</strong> which means they cannot be changed after they are created.

Since a string consists a sequence of characters, characters in a string can be accessed using the standard [ ] syntax. Python uses zero‐based indexing, so if <strong>s</strong> is ‘hello’, then <strong>s[1]</strong> is ‘e’. If the index is out of bounds for the string, Python raises an error. The <strong>len()</strong> function returns the length of a string. The ‘+’ operator can concatenate two strings.

<table width="0">

 <tbody>

  <tr>

   <td width="194">name = “Alice”type(name) print(name[3])</td>

   <td width="346"><em>#c</em></td>

  </tr>

  <tr>

   <td width="194">print(len(name))</td>

   <td width="346"><em>#5</em></td>

  </tr>

  <tr>

   <td width="194">print(name + ” Lee”)</td>

   <td width="346"><em>#Alice Lee</em></td>

  </tr>

 </tbody>

</table>




<h2>Basic   Terminologies</h2>

Python follows the following rules of <strong>character classification</strong>: <strong>whitespace = ‘ t
rvf’  </strong>

<strong>(Remark: Python whitespace includes space, tab, linefeed, return, vertical tab, and formfeed) ascii_lowercase = ‘abcdefghijklmnopqrstuvwxyz’ ascii_uppercase = ‘ABCDEFGHIJKLMNOPQRSTUVWXYZ’ </strong>

<strong>ascii_letters = ascii_lowercase + ascii_uppercase digits = ‘0123456789’ hexdigits = digits + ‘abcdef’ + ‘ABCDEF’ </strong>

<strong>octdigits = ‘01234567’ punctuation = r”””!”#$%&amp;'()*+,‐./:;&lt;=&gt;<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="1e215e">[email protected]</a>[]^_`{|}~””” printable = digits + ascii_letters + punctuation + whitespace </strong>

<strong><u>Remark</u></strong>: the above strings are defined in the <strong>string</strong> module of Python. <strong>         </strong>

<h2>String methods        in        str       class</h2>

The built‐in <strong>str</strong> class has many methods for manipulating text. The commonly used methods include:

<ul>

 <li><strong>lower()</strong>, <strong>upper()</strong>: returns the lowercase or uppercase version of the string. To know more about the functions, type <strong>help(str.lower)</strong> or <strong>help(str.upper)</strong> in the IPython console.</li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="541">s = “HkbUCs” <strong>print</strong>(s.upper()) <em>#HKBUCS </em><strong>print</strong>(s.lower()) <em>#hkbucs </em><strong>help</strong>(s.lower) <em>#don’t put () at the end of s.lower!</em></td>

  </tr>

 </tbody>

</table>




<ul>

 <li><strong>strip()</strong>: returns a string with special char (as specified by the function parameter, or by default whitespaces) removed from the start and end.</li>

</ul>

s1 = “******HkbUCs******” s2 = ”      Computer    ” <strong>print</strong>(s1.strip(‘*’))        <em>#HkbUCs</em> <strong>print</strong>(s2.strip())  <em>#Computer </em>




<ul>

 <li><strong>isalpha()</strong>, <strong>isdigit()</strong>,<strong>isspace(), isalnum(), islower(), isupper()</strong>: tests if all the string chars are in the various character classes. o <strong>isalpha(): </strong>Returns True if the string has at least 1 character and all characters are <strong><em>alphabetic</em></strong>, and False otherwise

  <ul>

   <li><strong>isdigit()</strong>: Returns True if the string contains only <strong><em>digits</em></strong>, and False otherwise o <strong>isspace()</strong>: Returns True if the string contains only <strong><em>whitespace</em></strong> characters, and False otherwise</li>

   <li><strong>isalnum()</strong>: Returns True if the string has at least 1 character and all characters are <strong><em>alphanumeric</em></strong>, and False otherwise</li>

   <li><strong>islower()</strong>: Returns True if the string has at least 1 cased character and all cased characters are in lowercase, and False otherwise</li>

   <li><strong>isupper()</strong>: Returns True if the string has at least 1 cased character and all cased characters are in uppercase, and False otherwise</li>

  </ul></li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="194">s1 = “HkbUCs” s2 = “1000” s3 = “1000.” s3 = ”           ” <strong>print</strong>(s1.isalpha())</td>

   <td width="346"><em>#True </em></td>

  </tr>

  <tr>

   <td width="194"><strong>print</strong>(s2.isdigit())</td>

   <td width="346"><em>#True </em></td>

  </tr>

  <tr>

   <td width="194"><strong>print</strong>(s3.isdigit())</td>

   <td width="346"><em>#False </em></td>

  </tr>

  <tr>

   <td width="194"><strong>print</strong>(s4.isspace())</td>

   <td width="346"><em>#True </em></td>

  </tr>

 </tbody>

</table>




<ul>

 <li><strong>startswith()</strong>, <strong>endswith()</strong>: tests if the string starts or ends with the given other string.</li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="252">s = “CS is fun!” <strong>print</strong>(s.startswith(“CS”))</td>

   <td width="289"><em>#True</em></td>

  </tr>

  <tr>

   <td width="252"><strong>print</strong>(s.endswith(“un!”))</td>

   <td width="289"><em>#True</em></td>

  </tr>

  <tr>

   <td width="252"><strong>print</strong>(s.endswith(“UN!”))</td>

   <td width="289"><em>#Case sensitive, False </em></td>

  </tr>

 </tbody>

</table>




<ul>

 <li><strong>find()</strong>: searches for the given other string within the original string, and returns the first index where it begins or ‐1 if not found.</li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="194">s = “CS is fun!” <strong>print</strong>(s.find(“fun”))</td>

   <td width="37"> </td>

   <td width="20"> </td>

   <td width="289"><em>#6 </em></td>

  </tr>

 </tbody>

</table>




<ul>

 <li><strong>replace()</strong>: returns a string where all occurrences of ‘old’ part have been replaced by ‘new’ part.</li>

 <li>= “CS is fun!”</li>

 <li>= replace(“CS”, “Computer Science”) <strong>print</strong>(t) <em>#Computer Science is fun! </em></li>

</ul>




<ul>

 <li><strong>split()</strong>: returns a list of substrings separated by the given delimiter.</li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="194">s = “CS is fun!” words = s.split(‘ ‘) <strong>print</strong>(words)</td>

   <td width="58"> </td>

   <td width="289"><em>#[‘CS’, ‘is’, ‘fun!’] </em></td>

  </tr>

 </tbody>

</table>




<ul>

 <li><strong>join()</strong>: opposite of split(), joins the elements in the given list together using the string as the delimiter.</li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="309">s = “”words = [‘CS’, ‘is’, ‘fun’, ‘!’] s = s.join(words)print(s)</td>

   <td width="231"><em>#CSisfun! </em></td>

  </tr>

  <tr>

   <td width="309">m = ” “.join(words)print(m)</td>

   <td width="231"><em>#CS is fun! </em></td>

  </tr>

 </tbody>

</table>




The following example shows how to remove the punctuations from a sentence using <strong>replace( )</strong> and then split the sentence into a list of words using <strong>split( )</strong>:

<table width="0">

 <tbody>

  <tr>

   <td width="541">myString = “He said, ‘Hi! Stop! Stop!'” import string <em># to access the string.punctuation</em> for c in string.punctuation: myString = myString.replace(c, ”)words = myString.split(‘ ‘) <em># split the sentence into words</em> print(words)</td>

  </tr>

 </tbody>

</table>




<h2>String Slices</h2>

The “slice” syntax is a handy way to refer to sub-parts of sequences (e.g., the substring of a string). The slice <strong>s[start:end]</strong> is the elements beginning at <strong>start</strong> and extending up to but <strong>not</strong> including <strong>end</strong>. For example, we have a string “Alice” stored in the variable <em>name</em>. With the slice syntax, we get:

   name[2:5] is “ice”;   name[0:3] is “Ali”;   name[2:] is “ice” too.

<h2>String Formatting   (A        Review          of         Lab1A            –          Example        2.2)</h2>

The string formatting operator % takes a printf‐type format string on the left <strong>(%d</strong> for int, <strong>%s</strong> for string, <strong>%f</strong> for float), and the matching values in a tuple on the right: <strong>format % values</strong>

For example:

text = “<em>%s</em>! You have a meeting with <em>%s</em> at <em>%d</em>:<em>%d</em> pm.” % (“Good Morning”,

“Alice”, 3, 30)

print(text)

<em># Good Morning! You have a meeting with Alice at 3:30 pm.</em>




Alternatively, we can use the <strong>format()</strong> function to format a string. With this function, we do not need to specify the data types in the format string. We replace the %d, %s, %f with a set of braces.  For example:

<table width="0">

 <tbody>

  <tr>

   <td width="541">text = “{0}! You have a meeting with {1} at {2}:{3} pm.”.format(“Good Morning”, “Alice”, 3, 30) <strong>print</strong>(text)<em># Good Morning! You have a meeting with Alice at 3:30 pm.</em></td>

  </tr>

 </tbody>

</table>




We can see that the result is the same as using % operator. Both formatters are great, there is no problem if you use either the % operator or the <strong>format()</strong> function.

More examples of the <strong>format()</strong> function:

‘<em>{0}</em>, <em>{1}</em>, <em>{2}</em>‘.format(‘a’, ‘b’, ‘c’)   <em>#a, b, c</em> ‘<em>{}</em>, <em>{}</em>, <em>{}</em>‘.format(‘a’, ‘b’, ‘c’)      <em>#a, b, c </em>‘<em>{2}</em>, <em>{1}</em>, <em>{0}</em>‘.format(‘a’, ‘b’, ‘c’)   <em>#c, b, a</em>

‘<em>{0}</em>, <em>{1}</em>, <em>{0}</em>‘.format(‘a’, ‘b’, ‘c’)   <em>#a, b, a</em>

‘<em>{0}</em>, <em>{1}</em>, <em>{0}</em>‘.format(‘a’, ‘b’)        <em>#a, b, a</em>

<h2>Exercise         1</h2>

Write a Python function that accepts a sentence and returns the first longest word. Assume the words in the string are separated by whitespaces.

Example:

Input = “Hello World Computer Science is fun”

Expected Output = “Computer”

<h2>Exercise         2</h2>

Write a Python program that accepts a string and <em>stepsize</em> which is an integer between 0 and 25. The function is able to create a Caesar encryption which transfers a character to the one which is <em>stepsize</em> away.

Caesar encryption example with <em>stepsize</em> of 3:




<h1>File     I/O</h1>

<h2>Read   a          File</h2>

In Python, before accessing a file, we need to use built‐in function <strong><em>open</em></strong><strong>()</strong> to open it which returns a <strong>file object</strong>. <strong><em>open</em></strong><strong>()</strong> usually takes two string parameters:<strong><em> filename</em></strong> and <strong><em>mode</em></strong>. After opening a file successfully, you can read its data by <strong><em>read</em>( )</strong> or <strong><em>readline</em>( )</strong> functions through the file object. After accessing the file, use <strong><em>close</em>( )</strong> to close the file. Study the following examples to learn how to use these functions.

Download the file demo.txt and put it in your python directory. Type the following statements:

<table width="0">

 <tbody>

  <tr>

   <td width="559">file1 = open(“demo.txt”, “r”) <em># file1 is a file object</em> content = file1.read() <em># read all data from file1 as a string</em>file1.close() <em># close file1. Now we cannot access demo.txt through file1</em> <strong>print</strong>(content)</td>

  </tr>

 </tbody>

</table>




There are four different modes for opening a file:

<ul>

 <li>“r”: opens a file for reading (default)</li>

 <li>“w”: opens a file for writing, truncating the file first (i.e., <strong>the old data will be lost!</strong>)</li>

 <li>“x”: creates a new file and opens it for writing</li>

 <li>“a”: opens a file for appending, creates a new file if the file does not exist.</li>

</ul>

By default, <strong>read( ) </strong>will read data till the end of the file if you do not specify the range. We can also control how many bytes of data to read by providing an integer argument, i.e., <strong>read(size)</strong>:

file1 = open(“demo.txt”, “r”) <em># open the file</em> s = file1.read(100) <em># read 100 bytes</em> <strong>print</strong>(s) <strong>print</strong>() s = file1.read(100) <em># read another 100 bytes</em> <strong>print</strong>(s) file1.<strong>close</strong>()

For text file, we can use <strong>readline( )</strong> function read a line, e.g.,

<table width="0">

 <tbody>

  <tr>

   <td width="559">file1 = open(“demo.txt”, “r”)s = file1.readline() <em># read a line from demo.txt, including the last ‘
’</em> <strong>print</strong>(s) <strong>print</strong>()s = file1.readline() <em># read another line from demo.txt</em> <strong>print</strong>(s) file1.<strong>close</strong>()</td>

  </tr>

 </tbody>

</table>




The following example shows how to read all lines from a file separately:

<table width="0">

 <tbody>

  <tr>

   <td width="559">file1 = open(“demo.txt”, “r”) s = file1.readline()while s != ”: <em># when reach the end of the file, s should become empty ”</em>     print(s)s = file1.readline() file1.close()</td>

  </tr>

 </tbody>

</table>




Another way to read lines from a file is through <strong>readlines( )</strong>, which save all lines in a file as a list of string. This is the most commonly used way to process a text file.

<table width="0">

 <tbody>

  <tr>

   <td width="559">file1 = open(“demo.txt”, “r”) lines = file1.readlines() file1.close()print(len(lines)) <em># check the number of lines in demo.txt</em> for s in lines: <em># iterate the list of lines</em>     print(s)</td>

  </tr>

 </tbody>

</table>




We can also use <strong>write( )</strong> function to write data into a file opened with “w” or “x” or “a”:

file1 = open(“demo.txt”, “a”) <em># </em>“<em>a</em>” <em>means we can append data at the end</em> file1.write(“Now we have something new!”) file1.close()




Try the following example, to find out what is the difference between mode <strong><em>a</em></strong> and mode <strong><em>w</em></strong>:

file1 = open(“demo.txt”, “w”) file1.write(“Now we have something new!”) file1.close()

<h2>Exercise         3</h2>

Write a function <strong>copy(x, y)</strong> that can copy a file <strong>x</strong> into another file <strong>y</strong>. Use demo.txt as the input to verify your function.

<strong><em>Hint</em></strong>: use functions open( ), read( ), write( ), and close( ).