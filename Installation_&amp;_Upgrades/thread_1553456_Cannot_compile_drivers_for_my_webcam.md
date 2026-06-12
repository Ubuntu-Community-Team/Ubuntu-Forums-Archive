---
title: "Cannot compile drivers for my webcam"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by snufk1n on 2010-08-15
I'm trying to compile the stk11xx module, although without any success. 
> adolf@laptop:~/Webcam$ cd stk11xx-2.1.0/
adolf@laptop:~/Webcam/stk11xx-2.1.0$ sudo make -f Makefile.standalone 
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [driver] Error 2What am I doing wrong? I've tried reinstalling the linux-headers without any luck.

EDIT:
I solved the problem by changing the following line in Makefile.standalone:
> $(MAKE) -C $(KSRC) SUBDIRS=$(PWD) modules
to 
> $(MAKE) -C $(KSRC) SUBDIRS=$(shell pwd) modules

I also installed the package exuberant-ctags before I managed to compile the driver.

When it was comiled and ready I run 
> sudo modprobe videodev
sudo insmod ./stk11xx.ko

Now everything works as supposed to. Hooray!

---

