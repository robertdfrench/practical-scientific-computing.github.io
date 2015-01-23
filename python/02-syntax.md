---
title: Basic Syntax
ordering: 2
layout: default
group: Python
type: tutorial
---

# Basic Python Syntax

Python is a human friendly, highly readable language that attempts to minimze
unnecessary cruft. Normally, each line forms a single instructional statement.
Using *number literals* and the built-in operators `+` (add) and `-` (subtract),
one can construct a simple instruction:

**In [1]:**

{% highlight python %}
# This is a line comment.
5 + 2 
6 - 3 # This is an inline comment.
{% endhighlight %}




    3



Notice there is **no line terminators** like as in other languages (C, for
instance). **Comments** are denoted by whatever follows a `#` keyword and can
occur anywhere on a line. Comments are ignored by the Python interpereter. There
are *no block comments in Python*. This is due to one of the language's core
philosophies:

    "Explicit is better than implicit".
    
By forcing every comment line to start with `#`, the developer must make a
concious choice to comment out multiple lines. Multiple instructions can be
placed on the same line if separated by the `;` operator as in:

**In [2]:**

{% highlight python %}
# Now both instructions are on the same line.
5 + 2; 6 - 3
{% endhighlight %}




    3



The line above will perform both instructions sequentially. Code run in an
interactive shell will only print the result of the last instruction processed,
but both operations are in fact being executed. We can verify this by forcing
each operation to print using the built-in `print` function (formerly a keyword
prior to Python v3), which sends it's argument to the standard output. Function
arguments are enclosed by parentheses.

**In [3]:**

{% highlight python %}
print(5 + 2); print(6 - 3)
{% endhighlight %}

    7
    3


 Like most programming languages, one can express numbers in a variety of ways
using number literals. Number literals can be of three types: either an integer,
a float, or a complex. Floats can be expressed in scientific notation with `e`
between the significant figures and the powers of ten. Python supports complex
numbers. Purely imaginary decimal literals are indicated with the suffix `j`.
Ordinarily, all numbers are expressed as decimals, but one can use prefixes to
denote hex (`0x`), binary (`0b`) or octal (`0o`) integers. Literal prefixes and
suffixes cannot be mixed.

**In [4]:**

{% highlight python %}
50       # 50 as a decimal integer
50.0     # 50 as a floating-point decimal
50.      # 50 again as a floating-point decimal
5.0e1    # 50 as a floating decimal in scientific notation
50j      # A purely imaginary 50
0x32     # 50 as a hexidecimal integer
0b110010 # 50 as a binary integer
0o62     # 50 as an octal integer
{% endhighlight %}




    50



Math operations are intuitive. The basic math operators are:

| Operator | Operation      | Syntax           | English Equivalent          | Notes                                      |
|:--------:|:--------------:|:----------------:|:---------------------------:|:-------------------------------------------|
| `+`      | Addition       | `a + b`          | "a plus b"                  | Overloaded for built-in types              |
| `-`      | Subtraction    | `a - b`          | "a minus b"                 |                                            |
| `*`      | Multiplication | `a * b`          | "a times b"                 |                                            |
| `/`      | Division       | `a / b`          | "a divided by b"            | Floating-point True division: `3/5 == 0.6` |
| `//`     | Floor Division | `a // b`         | "floor of (a divided by b)" | Floor division: `3/5 == 0; 5.0//2 == 2.0`  |
| `%`      | Modulus        | `a % b`          | "a mod b"                   |                                            |
| `**`     | Exponentiation | `a**b`           | "a to the power b"          |                                            |
| `-`      | Negation       | `-a`             | "negative a"                | Can be used to construct negative literals |

Math operators in Python work as they do in pen-and-paper math: they preserve
the most exact representation whenever possible. The can be checked using the
`type` built-in function which returns the argument's **type**. Again, the
possible types are integer, float, and complex.

**In [5]:**

{% highlight python %}
type(5)
{% endhighlight %}




    int



**In [6]:**

{% highlight python %}
type(2)
{% endhighlight %}




    int



**In [7]:**

{% highlight python %}
type(5 + 2)
{% endhighlight %}




    int



**In [8]:**

{% highlight python %}
type(2.0)
{% endhighlight %}




    float



**In [9]:**

{% highlight python %}
type(2.0j)
{% endhighlight %}




    complex



**In [10]:**

{% highlight python %}
type(5 + 2.0)
{% endhighlight %}




    float



**In [11]:**

{% highlight python %}
type(5 + 2.0j)
{% endhighlight %}




    complex



The order of operations follows the academic standard (PEMDAS: Parentheses,
Exponents, Multiplication, Division, Addition, Subtraction):

**In [12]:**

{% highlight python %}
5 * (2 + 3) - 3**2
{% endhighlight %}




    16



Here, we meet parentheses again. Parentheses have a number of uses in Python. As
earlier, they enclose function arguments. Here, they alter the order of
operations. In general, they make logical groups of their contents. These groups
always carry over new lines and are thus a way of splitting long lines:

**In [13]:**

{% highlight python %}
(5 + 3
 - 2)
{% endhighlight %}




    6



**In [14]:**

{% highlight python %}
type(5
     + 3 -2)
{% endhighlight %}




    int



So far, we've seen the number literals, the math operators, and a few built-in
functions. We have not yet seen any of the core keywords. Python has 33 defined
keywords.

### Core Keywords

<center>

|                     | &nbsp; | Keywords                                      |
|--------------------:| ------ |:----------------------------------------------|
| **Boolean Logic:**  | &nbsp; | `True`, `False`, `in`, `and`, `or`, `not`     |
| **Identities:**     | &nbsp; | `None`, `is`                                  |
| **Conditionals:**   | &nbsp; | `if`, `elif`, `else`                          |
| **Flow Controls:**  | &nbsp; | `for`, `while`, `continue`, `pass`, `break`   |
| **Abstraction:**    | &nbsp; | `class`, `def`, `return`, `lambda`, `yield`   |
| **Namespaces:**     | &nbsp; | `import`, `from`, `as`, `with`                |
| **Excpetions:**     | &nbsp; | `try`, `except`, `raise`, `finally`, `assert` |
| **Memory:**         | &nbsp; | `del`, `global`, `nonlocal`                   |

</center>

Relax: you don't need to memorize these now. We'll learn them as we go. Less
than half are used regularly and we'll focus on only the most important ones.
Which are the important ones? Importance generally decreases from left to right
and from top to bottom. Simple programs, for instance, rarely use the bottom two
rows of commands. We'll take time to discuss these keywords in detail later. I'm
showing you the table now because there a few things we should learn from this
list:

 * **These words are reserved**: they cannot be used as names for user-defined
     objects.
 * **True, False, and None are built-in unique *objects* **.  They are the only
     capitalized keywords.
 * **All instruction keywords are lowercase**. After the 3 built-in objects
     (True, False, and None), the remaining keywords are instructions.

Having seen the keywords, we can take a look at assignment.


## Variables and Assignment

Any object instance can be assigned to a variable name and in Python,
*everything is an object*. Assignment is governed principally by the binary `=`
operator.

The variable name given to an object must follow some rules:

 * It cannot be one of the core keywords. It is, however, legal to reassign the
     names ascribed to built-in functions (like `print`).
 * It cannot start with a number.
 * It cannot contain characters used in operators.
 * It is case-sensitive

The variable name *should* follow certain conventions (see PEP8 for reasoning):

 * It should use full descriptive words.
 * If a single character, it should be absolutely unambiguous in semantic
     meaning.
 * Avoid 'l' (lowercase letter el), 'O' (uppercase letter oh), or 'I' (uppercase
     letter eye) as single character variable names.
 * It should use underscores_to_separate_words.
 * Local variables should be lowercase_words.
 * Constants should be ALL_CAPITAL_WORDS.

Names like "electron_mass" and "muon_energy" are better than "em" or "me". No
one wants to come back to code a year later and try to figure out what "em" and
"me" mean in their code. Take time to write clear code now: your future self
will thank you.

Assignment in Python can be thought of as giving an alias to an object instance.
You can give multiple aliases to the same object instance. To show this, we can
use the built-in function `id()` which returns a unique number associated with
an object in memory (in fact, it's derived from the object's memory address).

**In [15]:**

{% highlight python %}
a_literal = 5  # Assign an instance of the literal '5' to the name 'a_literal'
print(a_literal, id(a_literal)) # print the value of 'a_literal' along with it's unique ID.
another_literal = a_literal     # Assign the object assigned to 'a_literal' to 'another_literal'
print(another_literal, id(another_literal)) # Look at that: both 'a_literal' and 'another_literal' have the same ID.
{% endhighlight %}

    (5, 21008696)
    (5, 21008696)


As you can see, reassigning an object doesn't create a new instance of the
object. Instead, both variables point to *the same object in memory*. For those
who are familiar with C and C++, assignment in Python is similar to references.
Those of you who haven't learned C or C++ yet will be well prepared having
learned Python first.

The fact that assignment 'aliases' objects when possible can lead to a couple
serious 'gotchas' with so-called 'mutable' objects like `lists` which we will
talk about later. Again, "Explicit is better than implicit": if you want to
instantiate a new object on assignment, you must do so explicitly!

Finally, most objects upon which the math operators can act (like numbers and
strings) support additional do-and-reassign operators. These can be used to
compactify a statement. The set of all assignment operators is tabulated below.


| Operator | &nbsp; Operation             | Syntax &nbsp; | Description                                       |
|--------------:|:--------------------------|:----------:|:------------------------------------------------------|
| `=`         &nbsp;  | &nbsp; Assignment                | &nbsp; `a = b`    &nbsp; | Assigns the name 'a' to the **object** 'b'            |
| `+=`        &nbsp;  | &nbsp; Add and Reassign          | &nbsp; `a += b`   &nbsp; | Equivilent to `a = (a + b)`                           |
| `-=`        &nbsp;  | &nbsp; Subtract and Reassign     | &nbsp; `a -= b`   &nbsp; | Equivilent to `a = (a - b)`                           |
| `*=`        &nbsp;  | &nbsp; Multiply and Reassign     | &nbsp; `a *= b`   &nbsp; | Equivilent to `a = (a * b)`                           |
| `/=`        &nbsp;  | &nbsp; Divide and Reassign       | &nbsp; `a /= b`   &nbsp; | Equivilent to `a = (a / b)`                           |
| `%=`        &nbsp;  | &nbsp; Modulus and Reassign      | &nbsp; `a %= b`   &nbsp; | Equivilent to `a = (a % b)`                           |
| `**=`       &nbsp;  | &nbsp; Exp and Reassign          | &nbsp; `a **= b`  &nbsp; | Equivilent to `a = (a**b)`                            |
| `//=`       &nbsp;  | &nbsp; Floor Divide and Reassign | &nbsp; `a //= b`  &nbsp; | Equivilent to `a = (a // b)`                          |


## Core Data Structures

Now that we know how to assign objects to variable names, we can talk about the
core Python data structures. They are:

 * Numbers (which we've seen)
 * `None`
 * Booleans (True and False)
 * Strings
 * Lists
 * Tuples
 * Dictionaries
 * Sets

We've seen the numbers already. Let's go through the rest in finer detail.


## The `None` type

In Python, `None` is a special constant object that represents an explicit lack
of value. It is a null value. It has type `NoneType`.

**In [16]:**

{% highlight python %}
type(None)
{% endhighlight %}




    NoneType



Functions with no explicit return value will return `None`. Default arguments or
object attributes are often initialized as `None` when not explicitly set. All
instances of `None` are identically equal and are literally the same instance.
While `None` is extremely useful, it can be somewhat abstract for beginners.
Don't worry about it for now: future examples will make it clear how to make use
of `None`. I only mention it now because it has certain implications for
Booleans.


## Booleans

Booleans are objects that have one of two possible values: true and false, 1 and
0, off and on, etc. The Python keywords include two boolean objects (True and
False) and a few boolean operators (in, and, or, not) that return either `True`
or `False`.

Both `True` and `False` are objects of the type 'bool'. Boolean types are
expected as arguments to some instructions like `if`. Comparisons between
objects return boolean types.

**In [17]:**

{% highlight python %}
type(True)
{% endhighlight %}




    bool



However, other types can be interpereted as booleans in certain contexts. While
Python will cast a non-bool type into a bool on it's own when necessary, we can
explicitly cast non-bool types into bools using the built-in `bool` contructor.

**In [18]:**

{% highlight python %}
bool(1), bool(0), bool(5), bool(-2), bool([]), bool([1, 2, 3]), bool(None)
{% endhighlight %}




    (True, False, True, True, False, True, False)



So what's happening here? `bool(1)` and `bool(0)` are understandably
interpereted as `True` and `False` respectively. But why is `bool(5)`
interperted as True? Because 5 is both a defined object and not explicitly
interpereted as `False`. `bool(-2)` is True for the same reason. All objects
that are defined and not strictly interpereted as `False` are considered `True`.

So what then is strictly considered `False`? Objects numerically equivalent to
0, empty *iterable sequences*, and `None`. This is a potential 'gotcha' when
checking if an object *exists*: you must make sure that it is not one of the
`False` cases. In the above example, the objects `[]` and `[1, 2, 3]` are
respectively empty and non-empty 'iterables' called 'lists'. More on lists in a
moment.

The keyword `not` negates a boolean.

**In [19]:**

{% highlight python %}
not True, not False
{% endhighlight %}




    (False, True)



The keyword `in` tests for an object's membership in an *iterable sequence*
(More on these in a moment). Below, we check to see if 1 is a member of the
'tuple' (1, 2, 3). It is, so True is returned.

**In [20]:**

{% highlight python %}
1 in (1, 2, 3)
{% endhighlight %}




    True



If we check to see if 5 is a member of the same sequence, Python tells us that
is is not.

**In [21]:**

{% highlight python %}
5 in (1, 2, 3)
{% endhighlight %}




    False



The binary `and` operator returns the logical conjunction of it's operands. We
can have Python return the truth-table:

**In [22]:**

{% highlight python %}
True and True, True and False, False and True, False and False
{% endhighlight %}




    (True, False, False, False)



Likewise, the binary `or` operator returns the logical disjunction of the
operands:

**In [23]:**

{% highlight python %}
True or True, True or False, False or True, False or False
{% endhighlight %}




    (True, True, True, False)



## Strings

Strings are containers for text. The can be constructed in several ways:

  * Single-line strings use quotation marks, either:
     * Wrapped in single quotes: 'Like this...'
     * Wrapped in double quotes: "...or like this!"
  * Multi-line strings use quotation marks in triplicate:
     * '''In triple-single quotes'''
     * or """in triple double quotes"""
  * They can be constructed from the string contructor `str`.

Why, you may ask, are there so many ways to write strings? Well, imagine if you
want a quotation mark character in your string:

**In [24]:**

{% highlight python %}
king_arthur = 'Arthur says "I am your king."'
print(king_arthur)
woman_responds = "Woman: 'Well I didn't vote for you.'"
print(woman_responds)
chock_full_of_quotes = '''"I've got to use a multiline string to handle all the quotes!"'''
print(chock_full_of_quotes)
string_from_a_number = str(2.54)
print(string_from_a_number)
{% endhighlight %}

    Arthur says "I am your king."
    Woman: 'Well I didn't vote for you.'
    "I've got to use a multiline string to handle all the quotes!"
    2.54


Notice how having several ways of denoting strings saves you from having to
escape characters. Single line strings must open and close on a single line or
be broken over lines using the '\' character. Multi-line strings can span
several lines. They will preserve carriage returns in the string.

**In [25]:**

{% highlight python %}
long_string = 'The quick brown fox jumped \
over the lazy dog.'
print(long_string)
{% endhighlight %}

    The quick brown fox jumped over the lazy dog.


**In [26]:**

{% highlight python %}
the_squat_rack = '''allows for a free-weight workout using
a barbell without the movement restrictions imposed
by equipment such as the Smith machine.'''
print(the_squat_rack)
{% endhighlight %}

    allows for a free-weight workout using
    a barbell without the movement restrictions imposed
    by equipment such as the Smith machine.


Strings are a type of *iterable container* and as such you can do some neat
tricks with them.

**In [27]:**

{% highlight python %}
("barbell" in the_squat_rack), ("curls" in the_squat_rack), 
{% endhighlight %}




    (True, False)



The `in` keyword can act on strings. As iterables, strings have a length that
can be retrieved with the built-in function `len`:

**In [28]:**

{% highlight python %}
len(the_squat_rack)
{% endhighlight %}




    130



The string `the_squat_rack` is 130 characters long. We'll learn more about
special iterable stuff when we discuss lists. Strings in Python is are objects
(*everything* in Python is an object), and they have a number of methods
available to simplify string operations. For those who are new to object-
oriented programming, we'll explain methods in detail later. For now, just think
of 'methods' as functions that are in some way bound to an object. To see what
methods and attributes an object has associated with it, you can 'introspect'
the object using the built-in `dir` function.

**In [29]:**

{% highlight python %}
dir(long_string)
{% endhighlight %}




    ['__add__',
     '__class__',
     '__contains__',
     '__delattr__',
     '__doc__',
     '__eq__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__getitem__',
     '__getnewargs__',
     '__getslice__',
     '__gt__',
     '__hash__',
     '__init__',
     '__le__',
     '__len__',
     '__lt__',
     '__mod__',
     '__mul__',
     '__ne__',
     '__new__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__rmod__',
     '__rmul__',
     '__setattr__',
     '__sizeof__',
     '__str__',
     '__subclasshook__',
     '_formatter_field_name_split',
     '_formatter_parser',
     'capitalize',
     'center',
     'count',
     'decode',
     'encode',
     'endswith',
     'expandtabs',
     'find',
     'format',
     'index',
     'isalnum',
     'isalpha',
     'isdigit',
     'islower',
     'isspace',
     'istitle',
     'isupper',
     'join',
     'ljust',
     'lower',
     'lstrip',
     'partition',
     'replace',
     'rfind',
     'rindex',
     'rjust',
     'rpartition',
     'rsplit',
     'rstrip',
     'split',
     'splitlines',
     'startswith',
     'strip',
     'swapcase',
     'title',
     'translate',
     'upper',
     'zfill']



There are a lot of methods in a string object. For now, don't worry about the
stuff starting with double underscores like `__add__`: Methods named this way
are ones that a user shouldn't ever call directly, even though you can. They are
meant to be used internally. To use an object's method, you access it by calling
`object_name.method_name`. We can find out more information about the string
object's methods using the built-in `help` function. Let's look at the help for
the `format` and `upper` methods:

**In [30]:**

{% highlight python %}
help(long_string.format), help(long_string.upper)
{% endhighlight %}

    Help on built-in function format:
    
    format(...)
        S.format(*args, **kwargs) -> string
        
        Return a formatted version of S, using substitutions from args and kwargs.
        The substitutions are identified by braces ('{' and '}').
    
    Help on built-in function upper:
    
    upper(...)
        S.upper() -> string
        
        Return a copy of the string S converted to uppercase.
    





    (None, None)



Looking at the above output, we see that `help` prints a string attached to the
method that explains what it does and it's syntax. Notice also that the return
value of the help function is a an instance of `None` meaning that all the help
function does is print the method's documentation string or "docstring".
All objects CAN have docstrings and it is good practice to include them in your
programming. They're easy to make and greatly improve the readability of your
code. We'll show how you can write them for your functions when we get there.

So how do we call a method? A first guess might be to call:

**In [31]:**

{% highlight python %}
long_string.upper
{% endhighlight %}




    <function upper>



But that didn't work. A method is a kind of function, and to call a function
requires parentheses around it's arguments. If the parentheses are omitted like
above, Python thinks you want to manipulate the method which is itself a type of
object. All the command above tells us that the function `upper` is, well, a
function called "upper". No surprises here. So to call the function, we must
wrap it's arguments with parentheses. The docstring for `string.upper` tells us
the method takes no arguments, so to call it we write:

**In [32]:**

{% highlight python %}
long_string.upper()
{% endhighlight %}




    'THE QUICK BROWN FOX JUMPED OVER THE LAZY DOG.'



So now you can find out what methods an object has and what they do with their
help docstrings. Some smart shells like IPython provide easy access to an
object's methods and docstrings with tab completion. As an aside, `format` is a
really useful string method, but it's rather advanced. We'll come to it again
later.

## Lists

Lists are among the most useful of Pythons built-in data structures. We've seen
some lists already. We can make a list by calling the `list` *constructor* (a
built-in function) or by enclosing and ordered set of comma-separated objects in
square braces:

**In [33]:**

{% highlight python %}
# An empty list
example_list = [] 
# Another empty list
another_example = list() 
# The list constructor takes an interable as it's argument.
constructed_list = list('Some string') 
# A list of the numbers 0-9.
some_numbers = list(range(10)) 
# Notice that the contents needn't be the same type.
mixed_content_list = [1, 2.0, 'three'] 

# We can even do wild things like
# a list inside a list inside a list inside a list!
listception = [1, 2, [3, 4, 5, [6, 7, 8, [9, 10]]]] 
  #  Notice that the dimensions of the sublists needn't
  #  be the same! This is much like a tree graph.
{% endhighlight %}

Let's see what we've done. Lists are iterables, so we can check a list's length:

**In [34]:**

{% highlight python %}
(len(example_list),
 len(another_example),
 len(constructed_list),
 len(mixed_content_list),
 len(listception))
{% endhighlight %}




    (0, 0, 11, 3, 3)



We can print the contents of a list:

**In [35]:**

{% highlight python %}
print(some_numbers)
{% endhighlight %}

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]


We can use iterable-aware keywords on a list:

**In [36]:**

{% highlight python %}
(2 in mixed_content_list,
 'two' in mixed_content_list,
 'three' in mixed_content_list)
{% endhighlight %}




    (True, False, True)



And we can access specific elements of a list. The following is true for all
iterable objects (including strings). We do this by way of square braces
containing the desired element's index appended to an iterable object. In
Python, iterable **indexes start from 0**!

**In [37]:**

{% highlight python %}
# New school iterable awesomeness.
print(mixed_content_list[2]) 
{% endhighlight %}

    three


This syntax is actually a means of using one those 'hidden methods' I told you
to ignore earlier. In this case, the `[]` syntax calls an object's `__getitem__`
method:

**In [38]:**

{% highlight python %}
mixed_content_list.__getitem__(2)
{% endhighlight %}




    'three'



We can get more information about `__getitem__` using help:

**In [39]:**

{% highlight python %}
help(mixed_content_list.__getitem__)
{% endhighlight %}

    Help on built-in function __getitem__:
    
    __getitem__(...)
        x.__getitem__(y) <==> x[y]
    


The help docstring tells us that the two methods are equivalent. Another thing
we can do with iterables is 'slicing'. Slicing uses similar syntax to getitem,
but a different argument:  2 indexes separated by ':' in the special notation:

**In [40]:**

{% highlight python %}
(some_numbers,
 some_numbers[0:5],  # Slice from index [0,5).
 some_numbers[:5],   # Another slice from index [0,5).
 some_numbers[3:5],  # A slice from index [3, 5).
 some_numbers[3:10], # A slice from index [3, 10)
 some_numbers[3:])   # A slice from index [3, infinity).
{% endhighlight %}




    ([0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
     [0, 1, 2, 3, 4],
     [0, 1, 2, 3, 4],
     [3, 4],
     [3, 4, 5, 6, 7, 8, 9],
     [3, 4, 5, 6, 7, 8, 9])



Python can even interperet negative indexes as counting from the end of the
list.

**In [41]:**

{% highlight python %}
(some_numbers,
 some_numbers[-2],
 some_numbers[-3:],
 some_numbers[:-3],
 some_numbers[-5:-2],
 some_numbers[3:-3])
{% endhighlight %}




    ([0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
     8,
     [7, 8, 9],
     [0, 1, 2, 3, 4, 5, 6],
     [5, 6, 7],
     [3, 4, 5, 6])



Be aware of this in case you use a malformed out-of-range index. Python lets you
do a lot of things that would be considered "dangerous" in other languages (like
C/C++). The philosophy behind this is summed up as:

    We are all consenting adults here.

Basically, the language authors trust that you'll be careful in exchange for
having the freedom to do what you want.

Speaking of doing things that we want, We can insert, append, remove, pop, and
sort lists (and most other iterables) using their methods:

**In [42]:**

{% highlight python %}
# Make an empty list.
method_examples = []
print(method_examples)

# Append something to it.
method_examples.append('appended') 
print(method_examples)

# Append something else.
method_examples.append(4)          
print(method_examples)

# Insert something at index 1
method_examples.insert(1, 'insertion') 
print(method_examples)

# Pop removes the last element from the list and returns it
popped_item = method_examples.pop()    
print(popped_item)
print(method_examples)

# Append some new stuff to the list.
method_examples.append(4)
method_examples.append(2)
print(method_examples)

# Sort in place.
method_examples.sort()         
print(method_examples)

# Remove doesn't take an index, 
#   instead it removes the first occurance of 4.
method_examples.remove(4)      
print(method_examples)
{% endhighlight %}

    []
    ['appended']
    ['appended', 4]
    ['appended', 'insertion', 4]
    4
    ['appended', 'insertion']
    ['appended', 'insertion', 4, 2]
    [2, 4, 'appended', 'insertion']
    [2, 'appended', 'insertion']


That sort is interesting. Python tries to be smart about the default case but,
when push comes to shove, you can override the sort method with your own
specific comparator. The messy list of operations above requires us to print the
list out after each operation because these methods all return `None` and modify
the list 'in-place'. This means that the list is 'mutated' without making a new
object. When an object supports this, it is called a 'mutable object' as opposed
to an 'immutable object' which cannot be changed without altering it's location
in memory. `lists`, `dictionaries`, `sets` and most objects are mutable;
`numbers`, `strings`, and `tuples` are immutable. This has important
consequences for lists as we can see below:

**In [43]:**

{% highlight python %}
# Let's make a new list. A new object is created.
first_list = [1, 2, 3, 4]   
# Let's assign another name to that list.
second_list = first_list    
# Let's mutate the second list by reassigning an item in it.
second_list[2] = 1          

# What are the contents of 'first_list' and 'second_list' now?
print(first_list, second_list)
{% endhighlight %}

    ([1, 2, 1, 4], [1, 2, 1, 4])


Here we see that the assignment operation `second_list = first_list` does not
copy the first list into a new object. Instead both names `first_list` and
`second_list` refer to the same object! Because lists are mutable, if you mutate
one, you'll mutate the other because the two variables are just names for the
same object. If we wish to make a copy, we must do so explicitly:

**In [44]:**

{% highlight python %}
# We create a new object.
first_list = [1, 2, 3, 4]       
# We use the list ctor to make a new list from the first one.
second_list = list(first_list)  
# Let's mutate the second list by changing an item.
second_list[2] = 1              

# What are the contents of 'first_list' and 'second_list' now?
print(first_list, second_list)
{% endhighlight %}

    ([1, 2, 3, 4], [1, 2, 1, 4])


This is extremely important to be aware of, especially in large programs and
especially in data analysis.

## Tuples

Tuples are another sort of iterable container. They are created by separating
objects with commas:

**In [45]:**

{% highlight python %}
my_tuple = 'a', 'tuple', 'is formed'
print(my_tuple)
{% endhighlight %}

    ('a', 'tuple', 'is formed')


You may have seen this done in previous examples to list multiple outputs on a
single line. Looking at the output, we see Python has put parentheses around the
output tuple. This is entirely superfluous: the parentheses only there to make
it clear where the tuple starts and stops. Notice then that the arguments to a
function are a tuple. The arguments to a list contructor like `[1,2,3]` are a
tuple. There are other ways to construct a tuple, like using the tuple ctor,
which will make a tuple out of an iterable:

**In [46]:**

{% highlight python %}
another_tuple = tuple(range(5))
print(another_tuple)
{% endhighlight %}

    (0, 1, 2, 3, 4)


Our first example with tuples makes a single object (the tuple) out of three. We
can go the other way making three objects from one using tuples:

**In [47]:**

{% highlight python %}
one, two, three = my_tuple
print(one)
print(two)
print(three)
{% endhighlight %}

    a
    tuple
    is formed


Any iterable can be cast over assignment to variables, as long as the number of
variables created is equal to the length of the iterable. Let's see it again:

**In [48]:**

{% highlight python %}
one, two, three = 'wut'
print(one)
print(two)
print(three)
{% endhighlight %}

    w
    u
    t


We'll make use of this extensively when we get to loops. As with other
iterables, we can access tuple elements by the getitem syntax:

**In [49]:**

{% highlight python %}
my_tuple[2]
{% endhighlight %}




    'is formed'



Tuples are immutable so unlike lists, we can't change them once their made:

**In [50]:**

{% highlight python %}
my_tuple[2] = 'is modified'
{% endhighlight %}


    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)

    <ipython-input-50-fa5b9e48f84e> in <module>()
    ----> 1 my_tuple[2] = 'is modified'
    

    TypeError: 'tuple' object does not support item assignment


Here we see the first example of a Python stack trace. When we issue a command
that gives rise to an error, the error is pointed out at runtime and a stack
trace is issued to help us debug the problem. Here, the error is a `TypeError`.
The error occurs on line 1 at `my_tuple[2] = 'is modified'` and the error tells
us that tuples don't support item assignment. Fancy words for "tuples are
immutable types". Strings are immutable iterables as well so while we can get a
string's items, we can't modify them:

**In [51]:**

{% highlight python %}
print(long_string)
print(long_string[4])
long_string[4] = 'Q'
{% endhighlight %}

    The quick brown fox jumped over the lazy dog.
    q



    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)

    <ipython-input-51-d1bdc3471de6> in <module>()
          1 print(long_string)
          2 print(long_string[4])
    ----> 3 long_string[4] = 'Q'
    

    TypeError: 'str' object does not support item assignment


## Dictionaries

Dictionaries are a type iterable container called a map. They use (key : value)
pairs to identify elements. They are unordered, which is to say they their
elements cannot be accessed by an index. Instead, elements are accessed by their
'key'. To create a dictionary, we can use the `dict` ctor or enclose a tuple of
(key : value) pairs in curly-braces. Keys are separated from their value by a
colon. Keys must be unique in the dictionary and must be immutable objects
(strings, number literals, tuples, etc.).

**In [52]:**

```Python
empty_dict = {}
what_colliders_collide = dict(lhcb='hadrons',
                              kekb='leptons',
                              tevatron=None)
mad_dict = {1:'first element',
            'twos':2222,
            'third key':[1, 2, 3],
            (4, 4):'value mapped by a tuple'}
```

**In [53]:**

{% highlight python %}
what_colliders_collide
{% endhighlight %}




    {'kekb': 'leptons', 'lhcb': 'hadrons', 'tevatron': None}



**In [54]:**

{% highlight python %}
mad_dict[1]
{% endhighlight %}




    'first element'



**In [55]:**

{% highlight python %}
mad_dict['twos']
{% endhighlight %}




    2222



**In [56]:**

{% highlight python %}
mad_dict['third key']
{% endhighlight %}




    [1, 2, 3]



**In [57]:**

{% highlight python %}
mad_dict[(4,4)]
{% endhighlight %}




    'value mapped by a tuple'



To see list of keys in a dictionary, one can use the `keys` method:

**In [58]:**

{% highlight python %}
mad_dict.keys()
{% endhighlight %}




    [1, (4, 4), 'twos', 'third key']



Notice that the keys are in a different order than how we constructed the
dictionary. In a dictionary *order does not matter*. The usual sequence keywords
apply to dictionary keys, but not values:

**In [59]:**

{% highlight python %}
1 in mad_dict, (4, 4) in mad_dict, 2222 in mad_dict
{% endhighlight %}




    (True, True, False)



## Sets

Nevermind sets. You can learn about them on your own. We've already seen the
more useful data structures.

## Comparison Testing

### Comparison Operators
| **Operator** | **Operation**               | **Syntax** | **Description** |
|--------------|-----------------------------|------------|-------------------------------------------------------|
| `==`         | Tests Equality              | `a == b`   | True if a is equivalent to b; False otherwise         |
| `!=`         | Tests Inequality            | `a != b`   | True if a is inequivalent to b; False otherwise       |
| `<>`         | Tests Inequality            | `a <> b`   | True if a is inequivalent to b; False otherwise       |
| `>`          | Tests greater-than          | `a > b`    | True if a is strictly greater than b; False otherwise |
| `<`          | Tests less-than             | `a < b`    | True if a is strictly less than b; False otherwise    |
| `>=`         | Tests Greater-than-or-equal | `a >= b`   | True if a is not less than b; False otherwise         |
| `<=`         | Tests Less-than-or-equal    | `a <= b`   | True if a is not greater than b; False otherwise      |

### Bitwise Operators
| **Operator** | **Operation**           | **Syntax** | **Description** |
|--------------|-------------------------|------------|-------------------------------------------------------|
| `&`          | Bitwise AND             | `a & b`    | Copies bit to result if 1 in both operands            |
| &#124;       | Bitwise OR              | a &#124; b | Copies bit to result if 1 in either operand           |
| `^`          | Bitwise XOR             | `a ^ b`    | Copies bit to result if 1 in only one operand         |
| `~`          | Bitwise Complement      | `~a`       | Returns inverted bits of a                            |
| `<<`         | Bitwise Shift Left      | `a << b`   | Shifts a to the left by b bits; b must be an integer  |
| `>>`         | Bitwise Shift Right     | `a >> b`   | Shifts a to the right by b bits; b must be an integer |
