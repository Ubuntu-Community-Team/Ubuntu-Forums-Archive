---
title: "How to fix No Display after Ubuntu 10.10 install"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by jfaberna on 2011-04-06
I hope this might help others. I had Ubuntu 10.04 installed on a Core i5 system with a Nvidia GE 9600 GSO card installed. When I upgraded to 10.10 in place I had no issues.

However, when I tried to install Ubuntu 10.10 directly from the LiveCD (either i386 or x64), on reboot, there was no display at all.

I found out that if I edit the grub kernel line at boot and add nomodeset and remove slash and quiet, it comes up in a degraded video mode allowing me to install the Nvidia Restricted Driver. Now when I reboot, I get the full desktop with the Nvidia driver working fine.

---

### Post by jfaberna on 2011-04-14
BTW, When I selected the restricted Nvidia driver to install, I picked the second one that had "recommended" by it and not the "current one". Neither were activated until I did it. That must be what changed in Ubuntu 10.10

Jim A

---

