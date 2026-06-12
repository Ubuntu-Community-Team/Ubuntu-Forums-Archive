---
title: "GRUB error 21"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by petrus bitbyter on 2007-05-03
Installed dapper drake on a machine with two disks and 1G memory. The primary master contains Win
2000, I have the slave (20G) free for the installation. After installation I reboot and get the message:

GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 21


Tried to boot from both disks (by BIOS menu), but got the same message. Installed again: same result. So what's wrong and what can I do?

petrus bitbyter

---

### Post by confused57 on 2007-05-03
Here's a description of grub error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

I once received this error with a slave drive that wasn't enabled, it was set to "off"...after resetting to "auto", I no longer received the error.   You could check your bios setting, maybe jumper settings on the hard drive, or possibly your IDE connection to the drive.

---

### Post by petrus bitbyter on 2007-05-03
gotcha, thanks

petrus bitbyter

---

