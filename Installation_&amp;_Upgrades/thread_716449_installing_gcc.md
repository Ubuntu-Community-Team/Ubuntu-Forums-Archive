---
title: "installing gcc"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by brindly on 2008-03-05
while giving ./configure i am getting following error

checking MACHDEP... linux2
checking EXTRAPLATDIR... 
checking for --without-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

plz tell me whether i need to install gcc

---

### Post by lloyd_b on 2008-03-05
> **brindly said:**
> while giving ./configure i am getting following error

checking MACHDEP... linux2
checking EXTRAPLATDIR... 
checking for --without-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

plz tell me whether i need to install gcc

It looks like *someting* is broken.  Try installing the package "build-essential" ("sudo apt-get install build-essential" in a terminal window, or use the package manager of your choice).  This should install EVERYTHING needed to compile programs.

Lloyd B.

---

