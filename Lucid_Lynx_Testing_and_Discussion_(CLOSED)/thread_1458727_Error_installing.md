---
title: "Error installing"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KaiJordanDay on 2010-04-20
> kai@kai-laptop:~$ cd acerhk*
kai@kai-laptop:~/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/kai/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
Makefile:303: /usr/src/linux-headers-2.6.32-21-generic/scripts/Kbuild.include: No such file or directory
Makefile:538: /usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [acerhk.ko] Error 2


When I ry and install acerhk, which i NEED for my wireless.
I've been trying for 2 days. If its not fixed in the next day im moving back to windows.

---

### Post by KaiJordanDay on 2010-04-20
Ok, so I reinstalled my linux headers

now I get this:

> kai@kai-laptop:~/Desktop/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/kai/Desktop/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [acerhk.ko] Error 2
kai@kai-laptop:~/Desktop/acerhk-0.5.35$ 



---

