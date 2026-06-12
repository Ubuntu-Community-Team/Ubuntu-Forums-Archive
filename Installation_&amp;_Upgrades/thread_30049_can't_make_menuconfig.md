---
title: "can't make menuconfig"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by itsme on 2005-04-27
i installed all necessary packages according the howto for kernel compiling.
but i can't make make menuconfig. it dosn't mather if i use menuconfig, gconfig etc.
i tried the kernel from kernel.org and unbuntu kernel source 2.6.10.

i get always the following message

/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh no such file or directory
make[1]: scripts/Makefile.build: no such file or directory
...
make: ***[scripts_basic] error 2

:(

any idea??

---

### Post by ape on 2005-04-27
From the error message it looks like not all the files are present in the linux source directory.  Do you in fact have a gcc-version.sh script under the scripts/ directory in the source tree?  What about the Makefile.build in the same location?

If they are there, are they readable by the account you are attempting to run make menuconfig with?

---

