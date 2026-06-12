---
title: "Tossim execution error - python2.5-config not found"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by deceaseddolphin on 2010-08-03
Hi all,

I installed tinyos-2.x in Ubuntu lucid. I tried to simulate tossim environment for simple Blink application using the command: make micaz sim 

and ended up with the following error:

mkdir -p simbuild/micaz
make: python2.5-config: Command not found
make: python2.5-config: Command not found
make: python2.5-config: Command not found
and
Python.h: No such file or directory
and
make: *** [sim-exe] Error 1

eventually installed python-old-doctools package which supposedly includes python2.5-config package but alas! It doesn't compile yet.

Any suggestions?

---

### Post by Mr.Carramba on 2010-08-27
add to apt-source list

```

deb [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) lucid main 
```

run

```

$ sudo apt-get update
$ sudo apt-get install python2.5 python2.5-dev python2.5-old-doctools python2.5-gdb

```

and you are upp and running

---

### Post by satterfield on 2011-01-17
I followed these instructions and now get the following error when I run sudo apt-get install python2.5 python2.5-dev python2.5-old-doctools python2.5-gdb:
 
E: Unable to locate package python2.5-old-doctools
E: Couldn't find any package by regex 'python2.5-old-doctools'
 
Please advise.
 
thanks,
 
steve

---

### Post by Mr.Carramba on 2011-01-18
try removing python2.5-old-doctools from command line, I personally don't use it.

---

### Post by deceaseddolphin on 2011-03-09
> **satterfield said:**
> I followed these instructions and now get the following error when I run sudo apt-get install python2.5 python2.5-dev python2.5-old-doctools python2.5-gdb:
 
E: Unable to locate package python2.5-old-doctools
E: Couldn't find any package by regex 'python2.5-old-doctools'
 
Please advise.
 
thanks,
 
steve
try this tutorial, should help you:

[http://docs.tinyos.net/index.php/TOSSIM#You_do_not_have_the_needed_Python_support_installed](http://docs.tinyos.net/index.php/TOSSIM#You_do_not_have_the_needed_Python_support_installed)

it is a path problem, all you need to find out is the python path where Python.h and libpython.2.x.so file (x=6 in my Ubuntu - python 2.6.6, yours might be different)

---

