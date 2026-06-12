---
title: "Python Installation"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by lovo on 2011-12-13
Hi
I wanted to install several versions of Python on my computer and I made a mistake.
I unzipped the python 2.5 sources, ran ./configure, make, make install.
By doing this, I thought I would install python 2.5 in this folder but it seems that I scratch my other python 2.7. For example, I can't run this line:
```
>>> from twisted.python.threadpool import ThreadPool
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named twisted.python.threadpool


```Where as it was working before. (can somebody confirm ?)

My current python:
```
$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2

```

I would like to go back to this working version :S
How can I do that?

If you have good links explaining the installation by compiling sources, I would like to read it because Im still unsure the full process.

---

### Post by MG&amp;TL on 2011-12-13
> **lovo said:**
> Hi
I wanted to install several versions of Python on my computer and I made a mistake.
I unzipped the python 2.5 sources, ran ./configure, make, make install.
By doing this, I thought I would install python 2.5 in this folder but it seems that I scratch my other python 2.7. For example, I can't run this line:
```
>>> from twisted.python.threadpool import ThreadPool
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named twisted.python.threadpool


```Where as it was working before. (can somebody confirm ?)

My current python:
```
$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2

```

I would like to go back to this working version :S
How can I do that?

If you have good links explaining the installation by compiling sources, I would like to read it because Im still unsure the full process.

I can't help with the problem (although I think there might be an apt option to not remove anything), but i can explain roughly the compilation process.

```
./configure
```

reads and executes the configure file, and executes scripts contained in that script to check that any libraries etc. are clean and installed. Google "GNU Autoconf" for more info on this huge topic

```
make
```

runs the GNU Make program (see "man make"), which first scans the folder for some permutation of "Makefile", then executes the instructions within that to compile any source files.

```
sudo make install 
```  

executes GNU Make again, this time looking for the "install" rule of the Makefile, which copies the compiled libraries and/or programs to the right places in your filesystem.

If you ever want to write Makefiles, there are some excellent short tutorials on the web, or the (somewhat weighty) GNU manual: [http://www.gnu.org/s/make/manual/make.html]("http://www.gnu.org/s/make/manual/make.html")

I hope this helps comprehension. :)

---

