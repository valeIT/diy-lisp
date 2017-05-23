## DIY Lang

> batteries included, some assembly required

In this tutorial/workshop we'll be implementing our own little language, more or less from scratch.

By the end of the tutorial you will be the proud author of a programming language, and will hopefully better understand how programming languages work  on a fundamental level.

### What we will be making

We will make a relatively simple, but neat language. We aim for the following features:

- A handful of data types (integers, booleans and symbols)
- Variables
- First class functions with lexical scoping
- That nice homemade quality feeling

We will *not* have:

- A proper type system
- Error handling
- Good performance
- And much, much more

The language should be able to interpret the following code by the time we are done:

```lisp
(define fact
    ;; Factorial function
    (lambda (n)
        (if (eq n 0)
            1 ; Factorial of 0 is 1
            (* n (fact (- n 1))))))

;; When parsing the file, the last statement is returned
(fact 5)
```

The syntax is very similar to languages in the Lisp family. If you find the example unfamiliar, you might want to have a look at [a more detailed description of the language](parts/language.md).

### Prerequisites

First, clone this repo.

```bash
git clone https://github.com/kvalle/diy-lang.git
cd diy-lang
```

Then, depending on your platform:

- **Mac**: Install [Python](http://www.python.org/), either from the webpage or using `brew`. Then run `easy_install nose` to install `nose`, the test runner we'll be using.

  *Optional: If you are familiar with [virtualenv](http://www.virtualenv.org/en/latest/) you might want to install `nose` in a separate pyenv to keep everything tidy.*
    
- **Windows/Linux**: Install [Python](http://www.python.org/), either from the webpage or your package manager of choice. Then install [Pip](https://pypi.python.org/pypi/pip). Finally, install `nose` like this: `pip install nose`.

  *Optional: If you are familiar with [virtualenv](http://www.virtualenv.org/en/latest/) you might want to install `nose` in a separate pyenv to keep everything tidy.*

- **Vagrant**: If you have [Vagrant](https://www.vagrantup.com/) installed, an easy way to get going is to use the provided `Vagrantfile`. Use `vagrant up` to boot the box, and `vagrant ssh` to log in. The project folder is synced to `/home/vagrant/diy-lang`.


#### Test your setup

Once installed, run `nosetests --stop` see that everything is working properly. This will run the test suite, stopping at the first failure. Expect something like the following:

```bash
$ nosetests --stop
E
======================================================================
ERROR: TEST 1.1: Parsing a single symbol.
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/nose/case.py", line 197, in runTest
    self.test(*self.arg)
  File "/home/vagrant/diy-lang/tests/test_1_parsing.py", line 15, in test_parse_single_symbol
    assert_equals('foo', parse('foo'))
  File "/home/vagrant/diy-lang/diylang/parser.py", line 17, in parse
    raise NotImplementedError("DIY")
NotImplementedError: DIY

----------------------------------------------------------------------
Ran 1 test in 0.034s

FAILED (errors=1)
```


### A few tips

Take the time to consider the following points before we get going:

- **Keep things simple**

  	Don't make things more complicated than they need to be. The tests should hopefully guide you every step of the way.

- **Read the test descriptions**

  	Each test has a small text describing what you are going to implement and why. Reading these should make things easier, and you might end up learning more.

- **Use the provided functions**

  	Some of the more boring details are already taken care of. Take the time to look at the functions provided in `parser.py`, and the various imports in files where you need to do some work.

- **The Python cheat sheet in `python.md`**

  	Unless you're fluent in Python, there should be some helpful pointers in the [Python cheat sheet](https://github.com/kvalle/diy-lang/blob/master/parts/python.md). Also, if Python is very new to you, the [Python tutorial](https://docs.python.org/2/tutorial/index.html) might prove helpful.

- **Description of your language**

  	Read a description of the language you are going to make in [language.md](https://github.com/kvalle/diy-lang/blob/master/parts/language.md).

### Get started!

The workshop is split up into eight parts. Each consist of an introduction, and a bunch of unit tests which it is your task to make run. When all the tests run, you'll have implemented that part of the language.

Have fun!

- [Part 1: parsing](parts/1.md)
- [Part 2: evaluating simple expressions](parts/2.md)
- [Part 3: evaluating complex expressions](parts/3.md)
- [Part 4: working with variables](parts/4.md)
- [Part 5: functions](parts/5.md)
- [Part 6: working with lists](parts/6.md)
- [Part 7: using your language](parts/7.md)
- [Part 8: final touches](parts/8.md)
