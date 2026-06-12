---
title: "Patching alsa drivers"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by risings0n on 2006-06-06
My intel HDA card needs a patch to unmute the front channels, which only 
applies to version 1.0.10 of alsa. This worked well with kernel 2.6.15-20 which i am running now. I have installed  linux-headers-2.6.15-23
and try to compile the alsa driver, but i get stuck with the following error.

make[2]: Leaving directory `/usr/src/alsa-driver-1.0.10/usb'
make[1]: Leaving directory `/usr/src/alsa-driver-1.0.10'
make -C /usr/src/linux SUBDIRS=/usr/src/alsa-driver-1.0.10  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-23/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/src/alsa-driver-1.0.10/acore/hwdep.o
/bin/sh: scripts/genksyms/genksyms: No such file or directory

I now have to revert to kernel 2.5.16-20 which breaks support for my Nvidia card - no xgl/compiz  :cry: 

anybody help?

---

