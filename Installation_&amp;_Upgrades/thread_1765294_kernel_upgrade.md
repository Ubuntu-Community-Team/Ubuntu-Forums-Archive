---
title: "kernel upgrade"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by harshisthere on 2011-05-22
I am using ubuntu 11.04 which has kernel 2.6.38-8 generic

but there is a newer version and update manager does not upgrade the kernel
is there any particular reason for this?

---

### Post by NormanFLinux on 2011-05-22
You need to install the 2.6.39.0 PPA in order to upgrade the kernel.

Install that first, do a sudo apt-get upgrade and then install the new kernel and reboot.

---

### Post by MAFoElffen on 2011-05-22
> **NormanFLinux said:**
> You need to install the 2.6.39.0 PPA in order to upgrade the kernel.

Install that first, do a sudo apt-get upgrade and then install the new kernel and reboot.
Look at post 2 of this sticky:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

There is a link there for the kernel maniline ppa, plus instruction on what to install. Look for the ones that say "natty."  You could install "others"... but that would be at-your-own-risk and the adventure is yours.

You could open sysnaptic and add natty proposed to your software sources (checkbox under updtaes)... reload and see what's there. You would updatel your flavor of linux-image...

Be advised that the 2.6.39.x tree is scheduled for onieric and by personally testing that as prelrelease (so far), that (IMHO) 2.6.39.2 is not stable yet.  but 2.6.39.1 was okay with a lot of things.

---

