---
title: "Please Help With Make Command"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by krisvamc on 2007-04-25
****

Hi,

**I tried to type make command  so that it will compile necessary  source files and create the executable program, but it showed the following error.**

Could anybody please tell how to rectify the error.

**The error is :**
[B]
XXX@xxxx:/home/xxxx/Desktop/mcs# make
g++ -ansi -pedantic -Wall -W -c mcs.cc
In file included from mcs.cc:54:
unp.h:43:59: error: sys/time.h: No such file or directory
make: *** [mcs.o] Error 1
[/B],

thanks


vamsi.

---

### Post by zvacet on 2007-04-26
```
sudo aptitude install build-essential
```

---

