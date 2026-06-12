---
title: "How to install g++4.1 in Ubintu 10.10"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by tommpogg on 2010-11-02
Hi,

I would like to install the g++4.1 compiler on my Ubuntu 10.10, bu the version 4.1 of g++ has been removed from the available packages (now starting from version 4.3).

Does anyone knows where can I retrieve and install g++4.1? (Possibly by using Synaptic)

Thank you

---

### Post by tommpogg on 2010-11-17
Hi, I solved the problem by manually installing g++-4.1. This is what I have done:

1) Install texinfo (e.g. apt-get install texinfo)
2) Download gcc-4.1.2 from [http://gcc.gnu.org/](http://gcc.gnu.org/) (gcc-4.1.2 contains g++-4.1)
3) Extract it and lauch "configure"; you can use the option --prefix=GCCPATH to set the installation path.
4) Open the Makefile and modify the line 

MAKEINFO = /opt/GNUARM/newlib-1.15.0/missing makeinfo
to
MAKEINFO = makeinfo

5) launch "make"
6) launch "make install"

Notice: steps 1 and 3 are required to fix a bug in gcc-4.1.2's installation files

It is a little bit complicated but it works!

---

### Post by dino99 on 2010-11-17
find it there:

[http://packages.ubuntu.com/search?keywords=gcc-4.1-multilib](http://packages.ubuntu.com/search?keywords=gcc-4.1-multilib)

---

### Post by tommpogg on 2010-11-24
> **dino99 said:**
> find it there:

[http://packages.ubuntu.com/search?keywords=gcc-4.1-multilib](http://packages.ubuntu.com/search?keywords=gcc-4.1-multilib)

Thank you for the suggestion.
The question is: do I have to download and install all the dependencies one by one?
If yes, I believe that a manual installation is faster.

---

