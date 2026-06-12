---
title: "X Libraries Missing"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by whitenerdy92 on 2007-12-08
When trying to configure a package, I received the following command line error:

> checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!


How do I add the X libraries?

---

### Post by taurus on 2007-12-08
Fire up synaptic from System -> Administration and Search for xorg.  You need to install the -dev package, xorg-dev.

---

### Post by whitenerdy92 on 2007-12-08
Thanks Ill tell u if that works

---

### Post by whitenerdy92 on 2007-12-08
Ok now when I 'make' I get this message:

> rj@rj-laptop:~/empire-client-4.3.10$ make
gcc -g -O2  -DHAVE_CONFIG_H -I.   -c -o termlib.o termlib.c
termlib.c:39:20: error: curses.h: No such file or directory
termlib.c:41:18: error: term.h: No such file or directory
termlib.c: In function &#8216;getsose&#8217;:
termlib.c:56: error: &#8216;OK&#8217; undeclared (first use in this function)
termlib.c:56: error: (Each undeclared identifier is reported only once
termlib.c:56: error: for each function it appears in.)
termlib.c:62: warning: assignment makes pointer from integer without a cast
termlib.c:63: warning: assignment makes pointer from integer without a cast
make: *** [termlib.o] Error 1


Could you tell me what this means? I've never successfully compiled a tar package before, mostly because I kept getting these sort of errors. I really appreciate this.

---

