---
title: "xwindow doesn't work"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by jcg on 2014-07-19
I have 12.04LTS (64B) I update according to "New hardware support..." installed automatically 3.13.0-32 (I had 3.8.0-42); no xwindows
I run on recovery mode falsake: error can't stat /etc/X11: switch to root and apt-get install --reinstall xserver-xorg; after that resume normal mode; Great all is good again.
/etc/X11 seems good. Reboot and... the same problem as before
What should I do? HELP

---

### Post by grahammechanical on 2014-07-19
You can try booting into that previous kernel (3.8.0-42). If you can still get to a desktop using Resume you can try changing video adapters. A lot of people have accepted this offer to upgrade the Hardware Stack and have got a broken OS as a result.

If using kernel 3.8.0-42 works, continue using it and every few days update and every few days try the kernel 3.13.0-32 or its replacement.

Regards.

---

### Post by jcg on 2014-07-19
thank you much; unfortunately, I got the same problem with 3.8.0-42 and 41. It seems it is more pernicious problem. Thank you anyway

---

### Post by jcg on 2014-07-19
I reinstalled lightdm and now it seems to work. I rebooted once and x is working. Cross your fingers.

---

