---
title: "upgrading the kernel from packages"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2008-03-19
After [this thread:](http://ubuntuforums.org/showthread.php?t=729211) I am trying to figure out how to upgrade my kernel from Synaptic (running Dapper) without breaking everything including some modules like nvidia-glx.  The other thread has all the details already typed out, but basically, I have 2.6.15-29-386 and I want to use 2.6.15-29-686 because this allows me to use both cores in my Core Duo T2600 processor.  When I try to boot that kernel, ti works fine but Xorg can't load because "nvidia" module can't load (isn't found) and I don't know how to make apt-get get the right version of nvidia-glx.  I'm also assuming there are toher packages that will die, but I dont' know how to make this upgrade work.

Any help?

---

### Post by nexus_2006 on 2008-03-20
Well I tried booting the 686 kernel and using any other display driver.  Nvidia-glx, nv, and vesa don't work with this 686 kernel.  How to I either force apt-get or synaptic to get the versions of software that I want it to get.  Can I go into Synaptic and tell it to throw out any package associated with the 386 kernel and load up the 686 equivalents?

---

### Post by nexus_2006 on 2008-03-20
Figured it out.  I had to install the linux-headers-version-686, linux-image-version686, linux, and linux-restricted-drivers-version-686 (I didn't know about this last one).

Anyway, it works fine now on 2 cores with all the old programs and such.  Thanks.

---

