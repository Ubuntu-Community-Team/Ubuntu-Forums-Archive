---
title: "memory usage off the charts?"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by tomhorsley on 2016-01-11
I test a lot of software by installing many many linux distros in KVM virtual machines. For some reason the ubuntu 15.10 32 bit (i686) machine (installed with the same memory and swap as previous versions of ubuntu) uses huge amounts of memory during the tests, triggers the kernel OOM processing, which eventually decides to kill off instances of sshd, thus terminating the tests which were running in an ssh session.

Are there known problems with kernel memory leaks? Or maybe a really inefficient malloc() implementation in 15.10?

The problem doesn't happen on the 64 bit 15.10. It also doesn't happen on previous versions of ubuntu all the way back to something like 8.

I'm running the exact same software in my tests on all these versions - nothing gets recompiled with new compilers.

I do NOT have any updates in this virtual machine, just the kernel and libraries shipped on the desktop iso.

---

