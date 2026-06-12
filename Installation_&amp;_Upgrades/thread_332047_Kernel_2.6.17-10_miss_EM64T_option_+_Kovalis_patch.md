---
title: "Kernel 2.6.17-10 miss EM64T option + Kovalis patch"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by ambrosa on 2007-01-05
I'm a new Ubuntu user.
I've installed Edgy 32 bit in my system (Intel Core 2 Duo E6600) and I want recompile kernel with EM64T specific gcc code (if any).
I use Edgy 32 bit version instead of 64 bit for the lack of various software/plugin in 64 bit world.
With Synaptics I've installed linux-source-2.6.17 package.

1)
Running make menuconfig, in "Processor Type and features -> Processor Family" there is not an entry about EM64T (only for Athlon64).
In OpenSuse 10.2 kernel there is this entry and I've recompiled its kernel without any problem and it runs fine.
I'm surprised to not find this options in Ubuntu kernel sources.
GCC 4.1.2 installed with Edgy has the options "mtune=nocona" or "mtune=prescott" used for best EM64T code generation. 

2) Do Ubuntu kernel source includes Con Kovalis patches ? If not, can be installed in kernel sorce tree without any problem ?

Thanks

---

