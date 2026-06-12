---
title: "upgrading from 10.10 to 11.04 bricked me"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by G3ML1NGZ on 2011-11-16
So a friend of mine came with his Toshiba Ac100 that had Ubuntu 10.10 installed. The OS offered the update to 11.04 and he said yes. the update froze and after 7 hours of that they tried shutting it off. Now it won't do anything.

this is what it shows me :

Using mmcblk3
Found /sbin/init , booting
[    31.024911]alignment trap: not handling instruction e8546f00 at [40041f1c]
[    31.025157]unhandled fault: alignment exception (0x011) at 0x409c44f5


after that it just stops and gives me tty1 login screen

I can't get it to boot up from a usb stick.


Any help would be greatly appreciated

---

### Post by raja.genupula on 2011-11-16
sometimes after new dist upgrades  issues like this going to occur , because of graphics driver problems.   
boot into recovery mode from grub and then boot into failsafex mode and then try to install graphics drivers , that gonna solve the issue.

all the best.

---

