---
title: "SunBlade150 Boot Problem"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by bndooley on 2006-12-19
I am attempting to install 6.10 server on a SunBlade 150.  When I boot from the CD, I get the dialogue to that asks whether I want to install or go into recovery mode.  I select install and the boot process tells me that it is creating a RAM disk.  A few seconds later, I get an illegal instruction error and am dumped back to the SunBoot ok prompt.

I tried this with 6.06 with the same result.  Any ideas what I shoud attempt next?

---

### Post by bndooley on 2006-12-20
After reviewing the lots of other threads, I've tried several things without success:

1) install server ide=nodma
2) install server mem=512
3) install server mem=512;ide=nodma

All still fail with the same illegal instruction error that dumps me back to OpenBoot.

I'm looking for a place to get the OBP upgrade for my box, but so far have not found it on the Sun site.

---

### Post by bndooley on 2006-12-20
I was able to upgrade my OBP to 4.17.1.  Now while loading the console output is a little more explicit:
.
.
.
Loading initial ramdisk (5260517 bytes at 0xDF802000 pjys, 0x40C0000 virt)...
       ERROR: Last Trap: Illegal Instruction

Error -256
       Error: Last Trap: Fast Datat Access MMU Miss

Error -256
Stack Underflow
ok

One again I tried
install server
install server ide=nodma
install server mem=512
install server ide=nodma;mem=512

Sam result with all.

---

