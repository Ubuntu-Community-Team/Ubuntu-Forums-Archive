---
title: "Repartitioned with gparted, GRUB lost, error 22"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by monocongo on 2008-05-03
I repartitioned my hard drive today in order to remove the Linux partitions and make everything NTFS again (converting a dual boot back to Windows only, using Ubuntu on another box instead).  Now the computer won't boot into Windows XP, apparently it was configured to use GRUB for booting and now that program is gone.  What can I do to get around this and have this machine boot into Windows XP again?  Do I want to somehow reinstall GRUB again, or is there a setting in the BIOS which I could change which would bypass the need for GRUB altogether?

Thanks in advance for any assistance.

--James

---

### Post by Pumalite on 2008-05-03
Super Grub will fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by MongooseCage on 2008-05-03
> **Pumalite said:**
> Super Grub will fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Yeah, SuperGrub FTW! I got like 2 CDs of that burnt. It definetly should do the trick

---

