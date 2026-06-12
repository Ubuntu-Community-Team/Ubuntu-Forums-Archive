---
title: "After Gutsy installation - running low-graphics mode?"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Artistar on 2008-01-03
A few hours ago i installed Gutsy for the first time, and after entering desktop Ubuntu offered me to enable/install restricted drivers that were available - i enabled them, and restarted the system. Now i can't get normal resolution, only 800x600 - i need 1680x1050. On booting Ubuntu is saying that it cannot recognize my graphic card (ATI HD2600XT), and is running in low-graphic mode.

What shall i do?

EDIT: btw, tried "dpkg-reconfigure xserver-xorg".... didn't work.

---

### Post by Pumalite on 2008-01-03
Do this:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver (you'll do better)
For the most part ATI does not support Linux. In any case, one IN the system, look for appropriate driver.

---

