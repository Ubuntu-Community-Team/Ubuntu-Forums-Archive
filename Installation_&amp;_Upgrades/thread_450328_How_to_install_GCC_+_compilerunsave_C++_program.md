---
title: "How to install GCC + compile/run/save C++ program"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by rajausman on 2007-05-21
Hi guys,

Does some have an easy guide, as how to install GCC compiler, and run and save a C++ program in Kbuntu 7.04, as i am very new to the world of Linux.....

Any suggestions are welcome.

---

### Post by lw5 on 2007-05-21
something like:
sudo apt-get install gcc

look at the manual pages of gcc:
man gcc

But what are you trying to do? Are you writing you own code? If so, have a look at [eclipse](http://www.eclipse.org/) (present in the repositories).

---

### Post by taurus on 2007-05-21
```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by rajausman on 2007-05-21
> **lw5 said:**
> something like:
sudo apt-get install gcc

look at the manual pages of gcc:
man gcc

But what are you trying to do? Are you writing you own code? If so, have a look at [eclipse](http://www.eclipse.org/) (present in the repositories).

I am trying to write C++ programs, that requires access to GCC. As i am ne4w to linux i really don't know, even how to edit/save/run a c++ program in linux by using gcc. Fair enough i can download gcc by using the command you have suggested, but what next ?.....again i am using kbuntu

---

### Post by Wim Sturkenboom on 2007-05-21
gcc is a compiler/linker and only does that. You use a normal editor (vi, gedit, nano etc) to create source files and next you compile them.

Below the very basic to compile/link (first line) and to run (second line)
```
gcc -Wall myfile.c -o myprogram
./myprogram
```

By the way, for C++ programs the compiler/linker is g++ (as far as I know; never use it).

---

