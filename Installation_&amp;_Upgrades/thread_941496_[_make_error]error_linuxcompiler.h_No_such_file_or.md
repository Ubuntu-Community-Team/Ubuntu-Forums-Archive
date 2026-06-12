---
title: "[ make error]error: linux/compiler.h: No such file or directory"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by thomasan on 2008-10-08
I was tring to recompile my kernel
but when i proceed to execute "make", it occurs such error:
-------------------
thomas@thomas-ubuntu7:/mnt/sda2/usagi/kernel/linux26$ make
CHK include/linux/version.h
make[1]: `arch/i386/kernel/asm-offsets.s' is up to date.
CHK include/asm-i386/asm_offsets.h
CHK include/linux/compile.h
CHK usr/initramfs_list
drivers/atm/../../include/asm/byteorder.h:5:28: error: linux/compiler.h: No such file or directory
CC drivers/eisa/eisa-bus.o
cc1: warnings being treated as errors
In file included from include/asm/mpspec.h:5,
from include/asm/smp.h:18,
from include/linux/smp.h:17,
from include/linux/sched.h:23,
from include/linux/module.h:10,
from include/linux/device.h:20,
from drivers/eisa/eisa-bus.c:10:
include/asm/mpspec_def.h:78: warning: ‘packed’ attribute ignored for field of type ‘unsigned char[6]’
drivers/eisa/eisa-bus.c:421: warning: pointer targets in initialization differ in signedness
drivers/eisa/eisa-bus.c:422: warning: pointer targets in initialization differ in signedness
make[2]: *** [drivers/eisa/eisa-bus.o] Error 1
make[1]: *** [drivers/eisa] Error 2
make: *** [drivers] Error 2
-------------------------------------
could anybody give me some suggestion? thanks very much!

---

