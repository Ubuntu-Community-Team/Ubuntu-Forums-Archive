---
title: "error: exception handling disabled, use -fexceptions to enable"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by manganganath on 2010-09-27
Hello,

I'm kind of new to Ubuntu. I want to compile ekiga 3.0.2 for ubuntu 10.04. But when I enter 'make' command in the terminal windows, it says that;

```

............
endpoints/opal-account.cpp:438: error: exception handling disabled, use -fexceptions to enable
make[3]: *** [opal-account.o] Error 1
make[3]: Leaving directory `/home/nuwang/ekiga-3.0.2/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/nuwang/ekiga-3.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nuwang/ekiga-3.0.2'
make: *** [all] Error 2

```I tried to solve the problem by setting CFLAGS = -fexceptions, in the Makefile. But it didn't work. Can someone please suggest me a way to overcome this problem?

Thanks in advance.

---

### Post by manganganath on 2010-09-28
problem is solved.

---

### Post by aemara on 2011-09-21
> **manganganath said:**
> problem is solved.

how did you solved it, i am facing the same problem now?

---

