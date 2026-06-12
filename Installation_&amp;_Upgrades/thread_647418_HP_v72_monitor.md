---
title: "HP v72 monitor"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by heatman on 2007-12-22
Hi, 

Just did a fresh install on a computer using a hp v72 monitor. Problem is xorg will only allow a resolution of 800x600, I've no problem using a resolution of 1024x768 in Windows and was wondering if I had to do something special to get xorg to display in the higher resolution.

Thanks.

---

### Post by jken146 on 2007-12-22
The command ```
dpkg-reconfigure xserver-xorg
``` is good for reconfiguring your X settings.  You may need to know what your monitor and graphics cards are capable of.

---

