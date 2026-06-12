---
title: "[FIXED] GL753VE Laptop cannot launch Linux Install or normal boot Linux Kernel."
date: 2017-09-28
forum: Installation &amp; Upgrades
---

### Post by danteslayer on 2017-09-28
Dear community,


I come here with a call for help, since I cannot find a solution for a problem that I have, and its annoying the hell out of me.


I also do not know if this is the right board where I can post this thread, so I apologize in advance if I post this in a wrong thread.


The problem is not so simple it seems, for it happens when I boot a USB or CD with a Linux system that I want to install on a drive that I have bought and included in the laptop.


The drive is a M2 SSD EVO (Link : [http://www.samsung.com/us/computing/...b-mz-n5e250bw/](http://www.samsung.com/us/computing/...b-mz-n5e250bw/) )


I have updated the firmware to the newest version, which is EMT21B6Q , and I updated the bios version of the model GL753 to Version 303, which is the newest version with the WinFlash program.


I have Included a picture of the error that appears whenever I boot from USB or CD and try to launch Linux Ubuntu without installing, or when I try to Install it OR when I diagnose the drive and check for errors.


I am getting totally clueless about that error, and I am hoping that someone can shine some hope and light upon these dark times that are upon me.


Thank you all in advance and have a nice day,


Daniel Nowak Janssen.[ATTACH=CONFIG]276870[/ATTACH]

---

### Post by danteslayer on 2017-10-03
Found the fix!

When booting to the GRUB, pressing e in the boot menu to edit the boot options and adding "nomodeset" to the end of the kernel line seems to fix the problem!

Anyway thank you all for helping, and have a nice day,

Daniel.

---

