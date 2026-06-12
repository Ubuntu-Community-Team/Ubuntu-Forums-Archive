---
title: "Kernel 4.4.21 LTS"
date: 2016-09-16
forum: Installation &amp; Upgrades
---

### Post by richolad-k on 2016-09-16
The above-referenced kernel was released today.  It may (might) resolve a regression I have experienced that keeps me from using Ubuntu 16.04.1 (believed to be an i915 driver issue).  To find out I need to try the kernel in Ubuntu.  If I install from an .iso and select the option to check for updates while installing, will I end up with the new kernel installed?

Thanks in advance for any certain, clear answers.

---

### Post by grahammechanical on 2016-09-17
My install of 16.04 is sitting on Linux kernel 4.4.0-38 generic

> graham@Ub1604:~$ uname -a
Linux Ub1604 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


> graham@Ub1604:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


Xenial (16.04) is still having daily ISO images built. So, you can either install 16.04.1 or the daily ISO image of 20160917 (17/09/2016). Even when we tick to install updates during the installation process we should also run update/upgrade afterwards. Sometimes there is more stuff to come down.

[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/131400/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/131400/downloads)

Regards

---

### Post by deadflowr on 2016-09-17
4.4.21 actually refers to the linux kernel LTS structure, not Ubuntu's LTS/Kernel structure, fer what it's worth.
You can get the Ubuntu build for it here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.21/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.21/")

Probably need to understand how to install development/upstream kernels, so here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")

---

