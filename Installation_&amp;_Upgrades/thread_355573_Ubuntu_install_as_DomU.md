---
title: "Ubuntu install as DomU"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by phixom on 2007-02-07
Hello

I'm trying to install ubuntu as a DomU instance. The Base-Dom0 System is a Fedora Core6 but will be switched to ubuntu in future. 
It's a amd64 version because there are some differences in the i386 Xen versions (pae, non pae). 
I've followed the instructions in the wiki articles but I was wondering, why I've should use a xen0-kernel-image? Is there no xenU image?
If I'm trying to use the xen0 images (2.6.16 and 2.6.17) ubuntu doesn't start.

2.6.17 give me a kernel-oops :

Unable to handle kernel paging request at ffff880000573020 RIP:
<ffffffff8025fd75>{cache_alloc_refill+836}
PGD 5ea067 PUD 5eb067 PMD 5ee067 PTE 573165
Oops: 0003 [1] SMP
CPU 0

and 2.6.17 says:

Bootdata ok (command line is  root=/dev/sda1)
Kernel command line:  root=/dev/sda1
VFS: Cannot open root device "sda1" or unknown-block(0,0)

If I use an other xenU kernel (selfcompiling) ubuntu starts perfect.
I want use a self compiled kernel because I'll use updates via apt in case of security risks.

Are there any solutions?

regards

alex.

---

