---
title: "Dual Boot problem (XP/Ubuntu) - UNMOUNTABLE_BOOT_PARTITION"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by evetsleep on 2005-09-05
I have been trying this multiple times and I can't seem to get Ubuntu to dual boot on my laptop (IBM Thinkpad T41).  I have a single hard drive and below  are the steps I take:
-Install Windows XP (up to SP2 and latest fixes) on 18gb of the 40gb drive (partition 18gb NTFS and leave 22gb of free space for Ubuntu).
-Intstall Ubuntu and let it slice up the free space as the installer sees fit.
-Boot Ubuntu and update all packages
-Reboot and attempt to log into Windows (using GRUB).  GRUB see's Window's just fine, but when I select Windows the Window's boot screen shows and then I get a blue screen of death with the message "UNMOUNTABLE_BOOT_VOLUME"

I am looking around for what the cause may be and how to fix it.  As things are now I have a working Ubuntu install (good!!) and a hosed XP install (bad).  Any suggestions on what the problem might be or what the best way is to create a clean dual boot (Ubuntu/Xp) setup would be awesome!

Thanks!

---

### Post by Steve1961 on 2005-09-05
Not sure why this is happening.  Can you paste the output of your grub configuration file here.  Just type cat /boot/grub/menu.lst in the terminal and copy and paste the output.  While you're at it, can you also paste the output of fdisk -l.

---

### Post by wabi on 2005-09-05
I am an absolute newbi, but remenber that this, (if I understood right) happens in slackware, and just have to run lilo again to set it up

[QUOTE=evetsleep]I have been trying this multiple times and I can't seem to get Ubuntu to dual boot on my laptop (IBM Thinkpad T41).  I have a single hard drive and below  are the steps I take:
-Install Windows XP (up to SP2 and latest fixes) on 18gb of the 40gb drive (partition 18gb NTFS and leave 22gb of free space for Ubuntu).
-Intstall Ubuntu and let it slice up the free space as the installer sees fit.
-Boot Ubuntu and update all packages
-Reboot and attempt to log into Windows (using GRUB).  GRUB see's Window's just fine, but when I select Windows the Window's boot screen shows and then I get a blue screen of death with the message "UNMOUNTABLE_BOOT_VOLUME"

I am looking around for what the cause may be and how to fix it.  As things are now I have a working Ubuntu install (good!!) and a hosed XP install (bad).  Any suggestions on what the problem might be or what the best way is to create a clean dual boot (Ubuntu/Xp) setup would be awesome!

Thanks![/QUOTE]

---

