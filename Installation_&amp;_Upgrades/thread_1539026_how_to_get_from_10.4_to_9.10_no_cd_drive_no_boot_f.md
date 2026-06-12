---
title: "how to get from 10.4 to 9.10 no cd drive no boot from usb"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by poundplay on 2010-07-26
its straight forward. i have a dell latitude c400. 10.4 keeps freezing and i think its because my graphics card is messing up. how can i 'roll back' to 9.10 without a cd drive and i cant boot from usb. please help.

---

### Post by lemming465 on 2010-08-15
There is no easy downgrade, sorry.  You could try switching to a more generic (and lower performance) video driver, such as "vesa". This would probably require something like:
1) boot using a recovery option
2) sudo Xorg -configure
3) edit /etc/X11/xorg.conf and change the driver to "vesa"

---

