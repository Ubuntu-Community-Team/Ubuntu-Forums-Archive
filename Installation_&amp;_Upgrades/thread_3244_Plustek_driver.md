---
title: "Plustek driver"
date: 2004-11-04
forum: Installation &amp; Upgrades
---

### Post by Pawel on 2004-11-04
I don't know where should i write about problem with driver instalation so, i'll write it here ;-).

It's very simple. When i try to making the driver with "make all" command, terminal shows sth. like this:

> 
[...]# make all
gcc -Wall -Wstrict-prototypes -fomit-frame-pointer -D_PTDRV_V1=0 -D_PTDRV_V0=41 -D_PTDRV_BUILD=6 -D__KERNEL__ -I/usr/src/linux/include -I./h -I./.. -O2 -DMODULE  -DMODVERSIONS -include /usr/src/linux/include/linux/modsetver.h -c src/misc.c - o obj/misc.o
In file included from /usr/src/linux/include/asm/processor.h:18,
                 from /usr/src/linux/include/linux/prefetch.h:14,
                 from /usr/src/linux/include/linux/list.h:7,
                 from /usr/src/linux/include/linux/wait.h:14,
                 from /usr/src/linux/include/linux/poll.h:8,
                 from h/plustek_sysdep.h:94,
                 from h/plustek_scan.h:61,
                 from src/misc.c:53:
/usr/src/linux/include/asm/system.h: In function `__set_64bit_var':
/usr/src/linux/include/asm/system.h:193: warning: dereferencing type-punned poin ter will break strict-aliasing rules
/usr/src/linux/include/asm/system.h:193: warning: dereferencing type-punned poin ter will break strict-aliasing rules
In file included from h/plustek_scan.h:167,
                 from src/misc.c:53:
h/plustek_types.h:189:8: warning: extra tokens at end of #endif directive
src/misc.c: In function `MiscRegisterPort':
src/misc.c:836: warning: implicit declaration of function `parport_enumerate'
src/misc.c:836: warning: assignment makes pointer from integer without a cast
src/misc.c:855: error: structure has no member named `next'
make: *** [obj/misc.o] B&#322;&#261;d 1


What should i do ?

Plustek Driver Version:  0.4.1.5
Ubuntu Version: 4.10
Kernel sources: yes :-)

thanks for your management ;-)

---

### Post by Pawel on 2004-11-24
Yes :-) - It's simple  8) 

It's enough to download the latest sane-backend from sane-project.org (it contains plustek drivers and many more (for example apple, microtek etc).

Next - read the doc sane, install sane-backend and make device:

mknod /dev/pt_drv c 40 0

-----------
Conclusion:

1. [www.google.com](www.google.com)
2. and just read the documentation  :p

---

