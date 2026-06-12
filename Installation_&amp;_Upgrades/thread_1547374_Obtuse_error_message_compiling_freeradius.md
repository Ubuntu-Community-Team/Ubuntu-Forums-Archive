---
title: "Obtuse error message compiling freeradius"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2010-08-06
This is for freeradius-1.1.7. 
I'm trying to compile freeradius to get around the missing rlm_eap_tls.so library, following/adapting the instructions in 
[this thread]("http://ubuntuforums.org/showthread.php?t=478804").

Now I'm stuck at an error that says:
/bin/bash: line 20: --with-rlm_sql_postgresql_lib_dir=/usr/lib/freeradius: No such file or directory 
/bin/bash: line 20: --with-rlm_sql_postgresql_include_dir=/usr/include/postgresql: No such file or directory 

The directories named DO exist.
The line numbers make no sense.

A script error, perhaps? Or, a badly worded error message that actually means something else?

Has anyone succeeded with this?

---

### Post by jcoles on 2010-08-07
The problem (one problem) turns out to be that # in column one is not actually a universal comment indicator. The exception is that when line continuation (\ at end of line) is in effect, it doesn't apply any more.

I had a ./configure statement with --<option> statements nicely formatted one per line using the line-continuation character and I commented out some options with "#". Moving the commented-out options to after the statement fixed that particular problem.

Now, I have the problem that the compile ends with the completely unhelpful statement:

make: *** [binary-arch] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
E: Building failed

Nonsense.  debian/rules is a text files, not a binary. And what the hell is "binary-arch". No such item on the machine. 
This is just about completely unsolvable!

Building from source ALMOST NEVER WORKS!

---

### Post by Bachstelze on 2010-08-07
What are you actually trying to do here?  That's now how you normally compile something from source.  You're trying to build a package, this is not a trivial task, and requires quite a lot of knowledge.

---

### Post by jcoles on 2010-08-07
I'd like to compile and install freeradius. 

Does reauthor, who wrote the How-To, not know what he's talking about?

What do you suggest? 

I tried the typical incantation:

./configure
make

But I just got different errors.

---

### Post by jcoles on 2010-08-07
I just got an inspiration and used the ./configure command line from [this other thread]("http://ubuntuforums.org/showthread.php?p=9689825") ($(confflags) removed and other variables replaced with actual values) and then did the usual routine:

make
make install

No errors. The executable is called radiusd and is not recognized by the service command. But I can run the server in debug mode. 

Progress!

---

