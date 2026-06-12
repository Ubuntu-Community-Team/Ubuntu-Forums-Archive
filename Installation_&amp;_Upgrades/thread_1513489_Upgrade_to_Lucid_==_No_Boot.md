---
title: "Upgrade to Lucid == No Boot"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by RecceDG on 2010-06-19
Did the auto-magic update to Lucid (from 9.10) using the Update Manager.

Result was a non-booting system. Gets as far as "Starting Up" and then hangs.

Played with GRUB menu, noticed that there were a few kernels installed:

2.6.32.22
2.6.32.21
2.6.31.22

Through process of elimination, determined that 2.6.31.22 works just fine. The two 2.6.32 kernels both hang.

Once the 2.6.32.21 kernel booted, but it only did so as I was holding down the power button to hard-reset. It won't do so reliably.

I suspect this has something to do with the VERY long-standing bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392) that has been plaguing me forever - although happily, the 2.6.31.22 kernel does NOT suffer from it and in fact boots very quickly.

It took a lot of work to get to this point. The whole upgrade to Lucid was the exact opposite of painless. At least I found a link on /. to move the window controls back to the proper corner of the window....

DG

---

### Post by wilee-nilee on 2010-06-19
Back it up and do a fresh install. When your trying to fix a broken upgrade you will not really ever be sure that you have fixed it. You may think your sure but, it will be a false hope.

---

### Post by RecceDG on 2010-06-20
The distro works fine; it is the kernel that is hanging.

100% reproducible.

DG

---

