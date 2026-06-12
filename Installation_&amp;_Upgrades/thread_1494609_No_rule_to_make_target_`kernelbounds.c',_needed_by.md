---
title: "No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'."
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by kcraj2 on 2010-05-27
hi all

im new to linux kernel programming, so help me
im getting this error when im tring to compile the hello world kernel module

**makefile has only one statement : **
   obj-m += hello.o

**im using this command to make**
   make -C /usr/src/linux-headers-2.6.34-020634-generic SUBDIRS= $PWD modules

**and the output is:**
make: Entering directory `/usr/src/linux-headers-2.6.34-020634-generic'
make: Nothing to be done for `/home/santosh/Work/Linux'.
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.34-020634-generic'

---

### Post by dino99 on 2010-05-27
****  linux-headers-2.6.34-020634-generic  *****

its already compiled  :confused:

---

### Post by @B6Mwu8fN9M on 2010-06-21
I think the problem is "make -C /usr/src/linux-headers-2.6.34-020634-generic SUBDIRS= $PWD modules"

$PWD is not defined. Try using $(shell pwd) instead.

Source: [http://forums.labjack.com/index.php?showtopic=4369](http://forums.labjack.com/index.php?showtopic=4369)

---

