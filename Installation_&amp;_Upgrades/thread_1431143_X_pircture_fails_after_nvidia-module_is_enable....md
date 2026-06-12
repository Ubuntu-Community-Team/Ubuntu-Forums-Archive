---
title: "X pircture fails after nvidia-module is enable..."
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by l4zy on 2010-03-16
Hello i've got really wierd problem with kernel 2.6.31-20. After kernel update nvidia-module crashes "picture" on gnome & kde, it gives random colors / pixels to the screen. U can use it, so it's somehow working. 
Without nvidia module everything work perfectly. I've tried 5 different drivers but no solution. Also reconfigured X (dpkg-reconfigure xserver-xorg). 

This problem is also with older kernels. Problem came after i rebooted to 2.6.31-20 kernel.

Any ideas about this problem

---

### Post by l4zy on 2010-03-17
Further testing showed that memorychips on gfxcards were broken.

---

