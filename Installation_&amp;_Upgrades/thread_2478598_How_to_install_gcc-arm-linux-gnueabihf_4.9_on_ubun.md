---
title: "How to install gcc-arm-linux-gnueabihf 4.9 on ubuntu 22.04 for arm 32 bit"
date: 2022-08-30
forum: Installation &amp; Upgrades
---

### Post by marietto2008 on 2022-08-30
Hello.

I'm running ubuntu 22.04 for arm32 on my arm chromebook snow :

```
mario@changeme:/etc/apt/sources.list.d# uname -a
Linux changeme 5.18.1-stb-cbe+ #1 SMP PREEMPT Sun Jun 5 14:16:07 CEST 2022 armv7l armv7l armv7l GNU/Linux

mario@changeme:/etc/apt/sources.list.d# lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```

I would like to know how can I install gcc-arm-linux-gnueabihf version 4 (maybe the 4.9 is good) on that os because I want to recompile the kernel 3.3 and it wants that. thanks.

---

### Post by MAFoElffen on 2022-08-31
To install the Arm GCC G++ crosscompiler and it's tool chain:
```

sudo apt-get install libc6-armel-cross libc6-dev-armel-cross binutils-arm-linux-gnueabi gcc-arm-linux-gnuabihf libncurses5-dev build-essential bison flex libssl-dev bc

```
The current version of gcc-arm-linux0gnuabihf under 22.04 is 4.11... That is part of the above...

---

