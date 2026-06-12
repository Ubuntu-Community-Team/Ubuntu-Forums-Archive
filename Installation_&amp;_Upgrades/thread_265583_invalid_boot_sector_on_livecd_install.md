---
title: "invalid boot sector on livecd install?"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by aquameta on 2006-09-26
First I tried to install Dapper from the live CD onto a logical partition of a sata drive, dual booting with XP.  No matter what, after install it just boots into XP.  So then I tried installing to the primary partition of a totally different drive, and setting that drive up as the boot drive in BIOS.  Then it says invalid boot sector.  

I read that Ubuntu is supposed to install grub and let you dual boot but I've had no such luck.  I've tried installing various boot managers (Gag, Grub) but when I try to boot to the linux partition it says the boot sector is invalid.  

Any ideas?

Thanks,
Eric

---

### Post by aquameta on 2007-03-19
Figured out the problem FINALLY, it was something wrong in the BIOS.  I reset my BIOS to default values, and now it works fine.  Very strange, still not sure what the BIOS setting was that was messing it up.

---

