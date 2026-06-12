---
title: "Making module"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by raajkhdf on 2009-11-24
Making module
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/ricky/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ricky/Desktop/vpnclient/linuxcniapi.o
In file included from /home/ricky/Desktop/vpnclient/Cniapi.h:15,
                 from /home/ricky/Desktop/vpnclient/linuxcniapi.c:31:
/home/ricky/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/ricky/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/ricky/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
ricky@ricky-laptop:~/Desktop/vpnclient$

---

### Post by SIGTERMer on 2009-11-24
> **raajkhdf said:**
> 
In file included from /home/ricky/Desktop/vpnclient/Cniapi.h:15,
                 from /home/ricky/Desktop/vpnclient/linuxcniapi.c:31:
**/home/ricky/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’**
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here


if you're the coder: you redefined 'uintptr_t'(defined in types.h). change the name.
if you're not the coder: there's a bug in the code, or -less likely- something very weird is going on..

---

