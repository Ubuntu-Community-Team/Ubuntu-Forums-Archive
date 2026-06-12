---
title: "Building a custom kernel fails"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by DarkBabar on 2006-12-06
I'm trying to build a custom kernel for low latency audio.
This is the tutorial I'm following: [https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption](https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption)
The only thing I've changed is the Linux kernel and patch version, from 2.6.16 to 2.6.19.
I get this error message.
```
  Building modules, stage 2.
  MODPOST 1738 modules
WARNING: Can't handle masks in drivers/ide/pci/atiixp:FFFF05
WARNING: "pm_send_all" [arch/i386/kernel/apm.ko] undefined!
WARNING: "pm_active" [arch/i386/kernel/apm.ko] undefined!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19-rt6'
make: *** [debian/stamp-build-kernel] Error 2
```
I have no idea how to proceed, so please help me.

---

### Post by h.aling on 2007-02-03
Maybe try to add "-fno-stack-protector" to the kernel's Makefile... It solved my build error with 2.6.17-ck1.

Around line 309 in mine:
```
CFLAGS          := -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
                   -fno-strict-aliasing -fno-common **-fno-stack-protector**
```

Cheers!

-H-

---

