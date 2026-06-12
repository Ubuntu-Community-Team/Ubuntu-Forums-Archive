---
title: "where is g77??????"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by sephora on 2008-10-31
Hi everyone!

I installed Intrepid today.

Everything went perfect, even the "turn off" and "restart" buttons worked perfectly:), until I tried to install g77 (fortran 77) because I use it for running programs for numeric calculations.
It isn't in the repositories:confused:. Can anybody help me to install it?



Best regards....

Thank you:lolflag:

---

### Post by Partyboi2 on 2008-10-31
Try downloading the deb package from [[COLOR=Blue]here[/COLOR]]("https://launchpad.net/ubuntu/intrepid/i386/g77-3.4/3.4.6-6ubuntu3") and installing it by double clicking on it.

---

### Post by sephora on 2008-11-01
Hi!

I tried to install g77 using the deb package but it didn't work. I got an error saying that a dependency is not satisfiable, specifically with the package gcc-3.4. This is strange because I have this program installed....

Does anybody know another way to install g77?


Greetings

---

### Post by Sorivenul on 2008-11-01
gfortran has replaced g77.  
Try it.  Hope it works for you.

---

### Post by Partyboi2 on 2008-11-01
deleted

---

### Post by khayyam37 on 2008-11-02
> **Sorivenul said:**
> gfortran has replaced g77.  
Try it.  Hope it works for you.

ugh. no, it doesn't. it seems this was once in the release notes, but no more. i wish it still were, would have saved me a lot of trouble.

---

### Post by Sorivenul on 2008-11-02
I'm not sure, then.  I forgot that you were looking for Fortran 77 not 95.
Have you tried fort77?  It invokes f2c like a real Fortran compiler, and should be able to handle your 77 code.  If it doesn't I'm at a loss on this one.

---

### Post by nhmc on 2008-11-12
fort77 is not a replacement for g77.  I have fortran 77 code that compiled without any problems using g77 that fort77 does not compile.

---

### Post by Sorivenul on 2008-11-12
Okay, did some more research.  
You may need to install the older version of the gcc, 3.4, which is in the repositories:
```
sudo apt-get install gcc-3.4
```

Apparently this should contain what you need to get going.

However, searching the Ubuntu package site showed [this]("http://packages.ubuntu.com/hardy/g77"), as well.
If you have the Universe repositories enabled you should be able to install it.

Good luck!

---

### Post by swhit on 2008-11-12
If fort77 is in the repositories (it does install and does appear to work as I tried fort77 with a few simple programs), why can't g77 be included? This doesn't make any sense to me.

---

### Post by sayantandas on 2008-12-04
i tried installing from the repos of hardy heron. g77 doesnt install. although gcc and cpp r installed , g77 shows unresolved dependencies. 
any idea?

---

### Post by abouzar on 2009-09-15
The problem is caused by the new version of gcc which is incompatible with g77-3.4.

I found that you can still use the old g77-2.95 compiler properly. In order to install it, I followed the below steps.

First, make sure you have the following repositories:

```
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security restricted main
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe multiverse
deb http://ftp.de.debian.org/debian etch main

```You can compare these with your source list by checking:

```
$ cat /etc/apt/sources.list
```If any of the repositories are not available, add them to the source list.

Then try

```
$ sudo apt-get update
```and then try:

```
$ sudo apt-get install g77-2.95
$ sudo apt-get install g77-2.95-doc
```Then you can create symbolic links to mach g77:

```
$ cd /usr/bin/
$ sudo ln -s g77-2.95 g77
$ cd /usr/share/man/man1
$ sudo ln -s g77-2.95.1.gz g77.1.gz

```Now, you can have the older version of g77 as your Fortran compiler. You can also see the man-pages.

Enjoy :P

> **sephora said:**
> Hi everyone!

I installed Intrepid today.

Everything went perfect, even the "turn off" and "restart" buttons worked perfectly:), until I tried to install g77 (fortran 77) because I use it for running programs for numeric calculations.
It isn't in the repositories:confused:. Can anybody help me to install it?



Best regards....

Thank you:lolflag:

---

