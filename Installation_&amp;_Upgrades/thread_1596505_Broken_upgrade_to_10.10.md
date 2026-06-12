---
title: "Broken upgrade to 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by aleeming on 2010-10-14
I have just upgraded to Ubuntu 10,10, which apparently went well on my AMD Athlon 64 3000+ Carrera Desktop. After the required re-boot, I have a frozen machine for the 26.35.kernel with the message:
Gave up waiting for root device. Common Problems:
-Boot args (cat/proc/cmline)
   -check rootdelay
   -check root
-Missing modules (cats /proc/modules; ls /dev)
ALERT! /dev/disk/by -uuid/0d5c0887....etc..  does not exist
Dropping to a shell
BysyBox v1.15.3 .......
(inittransfs) _

I can boot into the previous kernel 2.6.32-25 generic(x86_64).
Any idea what has gone wrong, & how do I resurrect the 2.6.35 kernel?
Thanks, Andrew

---

### Post by dino99 on 2010-10-14
i've got some bad issues with 2.6.35 too, and seen other users having too, so i've installed 2.6.36 from xedgers ppa and it works smoothly (only install the kernel packages, then desactivate this ppa)

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by aleeming on 2010-10-16
Thank you Dino99. I have have now upgraded to 2.6.35, and it is working fine.
Andrew

---

