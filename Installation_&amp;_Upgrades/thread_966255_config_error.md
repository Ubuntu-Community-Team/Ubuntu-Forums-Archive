---
title: "config error?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by zuheyr on 2008-11-01
Hello,

The 8.10 installation went perfectly well for my Dell desktop Inspiron 530s intel core 2 duo. Great except for wireless connection but I think I can solve it later. It is my fault in router conf probably.

However, I have a problem and this seems to be a potential problem for 64 bit machines...

uname -a output:
Linux zuheyr-desktop 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

I am trying to install dateshift and I get errors from configure !

< some lines deleted>
==================================================================

checking host system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking for ranlib... ranlib
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
updating cache ./config.cache
ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.
configure: error: libtool configure failed

========================================================================

Could you help me please?

Thanks for reading, regards, zuheyr

---

### Post by JohnsonCT on 2008-11-08
I managed to get this working by using the following command:

```
./configure --target=x86_64-unknown-gnu
```

Hope that helps.

---

