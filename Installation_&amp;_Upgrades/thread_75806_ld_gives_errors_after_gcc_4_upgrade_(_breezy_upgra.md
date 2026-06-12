---
title: "ld gives errors after gcc 4 upgrade ( breezy upgrade )"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by solatis on 2005-10-14
Hello,

Last night, I upgraded my system to breezy, which has gcc 4.0.2 shipping with it... I have some C++ projects I worked on, and sure, I had to change some code ( templates are a bit different ) and some other things... but for some reason, linking goes bad too, and I have *no* idea what's causing it.

Here is the error I get from ld:

> /lib/libpthread.so.0: undefined reference to `__libc_stack_end@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.0.2/../../../../lib/libm.so: undefined reference to `_rtld_global_ro@GLIBC_PRIVATE'
collect2: ld returned 1 exit status

and I have no idea how to fix this... this looks like a version ismatch between my glibc and gcc or something, something like gcc being built against a different version or something... anyway, anyone has any idea at all how to fix this, or where to look for more information on how to fix this ?

I'm trying these forums first, since I have this problem since my upgrade to breezy... if I should look at other support sources (for example, gcc's), please tell so... :)

---

### Post by solatis on 2005-10-15
So no one has any ide what's causing this problem ?

---

### Post by solatis on 2005-10-16
If no one knows how to fix it, can anyone *please* tell me where to go next ?

At the moment, I've done a clean breezy install and the problem still persists... I've submitted a bug report, but the devs don't really respond to it, the irc channel devs tell me to submit a bug report, no one seems to be able to help...

I'm getting really deserate, haven't been able to work for 3 days and at the moment am really regretting my upgrade to breezy... :(

---

### Post by solatis on 2005-10-16
By the way, I've created this really simple test case:

```
lmergen@breezy:~/svn/tsukku/doc/research/Prototypes/gcc $ cat test.cpp
#include <iostream>
int main () {
        std::cout << "Starting test" << std::endl;

}
lmergen@breezy:~/svn/tsukku/doc/research/Prototypes/gcc $ make clean && make
rm -f test.o test
g++ -c -Wno-deprecated -g -fno-inline -O0 test.cpp
g++ -o test -Wno-deprecated -g -fno-inline -O0 test.o
/lib/libc.so.6: undefined reference to `__libc_stack_end@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.0.2/../../../../lib/libm.so: undefined reference to `_rtld_global_ro@GLIBC_PRIVATE'
collect2: ld returned 1 exit status
make: *** [test] Error 1
lmergen@breezy:~/svn/tsukku/doc/research/Prototypes/gcc $
```

Looks to me like nothing could be wrong on my side... note that this is with a clean breezy install, i've done no additional configuration except apt-get install g++ on this system...

---

### Post by Perfect Storm on 2005-10-16
try:
Install gcc-3.4
then before compiling
```

CC=gcc-3.4
export CC

```

It could be a bug in gcc 4.0

---

