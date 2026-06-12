---
title: "Trying to compile a driver for ELO Touch Screen"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by computergroove on 2007-01-11
I am trying to compile the driver for an elo touch screen monitor. I have followed the directions given by Elotouch systems and I get to a point where I get the following errors:

user@user-desktop:/home/elocontrol$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/elocontrol modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /home/elocontrol/main.o
In file included from /home/elocontrol/main.c:10:
/home/elocontrol/elocontrol.h:12:19: error: ctype.h: No such file or directory
make[2]: *** [/home/elocontrol/main.o] Error 1
make[1]: *** [_module_/home/elocontrol] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [default] Error 2

How do I install the libraries to include the ctype.h header?

Thanks

---

