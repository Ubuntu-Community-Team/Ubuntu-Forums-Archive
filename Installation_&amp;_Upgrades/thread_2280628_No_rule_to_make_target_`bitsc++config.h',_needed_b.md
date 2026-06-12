---
title: "*** No rule to make target `bits/c++config.h', needed by, make error"
date: 2015-06-01
forum: Installation &amp; Upgrades
---

### Post by bolenedisatyanarayana on 2015-06-01
hi all,

I could not able compile my code, which was working fine on ubuntu 10.04 But not on **ubuntu 14.04** when i run make.
I am compiling with the CROSS_COMPILE flag.
```
CROSS_COMPILE=/opt/ELDK42/usr/bin/ppc_85xx-
```

any one help me on How to fix, it?:confused:
I've been searching on net from few days, didn't find any clue yet.


Tried by adding include file this way: 
```
-I/opt/ELDK42/ppc_85xx/usr/include/c++/4.2.2
```/
Then, it gave the following error: :mad:
```
/opt/ELDK42/ppc_85xx/usr/include/c++/4.2.2/iostream:44:28: error: bits/c++config.h: No such file or director
```

any help is heartly appreciated... :p:):)

**System details:**
Ubuntu 14.04, 32 bit
ELDK42, gcc --version 4.2.2

---

