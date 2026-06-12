---
title: "Unable to startup with Ubuntu LiveCD"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by TonyLechner on 2007-09-11
I just got to college, where they give everyone the same laptop.
I use Ubuntu at home, and the CD I used to install it worked fine there, but attempting to boot the live CD from these laptop (HP Compaq nw8440's) makes "X" crash to console on boot, and I can't even get into ubuntu.

The school support desk had me modify xorg.conf (sudo nano /etc/X11/xorg.conf) to include "HorizSync 26,28" and "VertRefresh 43,60" in the monitor section of that file, but when I run starx I get a "No Devices Detected" error.

The laptops all have ATI Mobility FireGL V5200 cards on PCI Express bus 1:0:0

***Any ideas?***

---

### Post by Pumalite on 2007-09-11
Try the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below 'Start Download'

---

