---
title: "Ubuntu Install Partition Troubles"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by Shoie13 on 2007-01-18
I'm attempting to install Ubuntu to my harddrive without the need to reinstall Windows and repartition.  I defragged and rebooted with LiveCD and the option on the installer to "resize" your partition for the Ubuntu install is not available. What must I do to get this option?

Also, I tried using the ubuntu.exe torrent mentioned in another topic that is supposed to run without the need to repartition, and when attempting to run Ubuntu, I received a message stating there was a mount error?

What I'm asking for is a solution to my resize problem, or a stable solution to install and run Ubuntu in a dualboot configuartion with Windows XP without the need to reinstall Windows. Any help or tips are appreciate. Thank you.

---

### Post by kingmonkey on 2007-01-18
I think this is to do with the resizing NTFS partitions. 

Gnome patition editor liveCD works really well for this. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Can I also point out that resizing a partition is repatitioning, so be sure you know what your doing.

---

### Post by Shoie13 on 2007-01-18
Do I run that on Windows or within Ubuntu or what?

---

### Post by TheWizzard on 2007-01-18
> **Shoie13 said:**
> Do I run that on Windows or within Ubuntu or what?
you can boot from the gparted live cd

just burn the cd, put it in and reboot.
make sure your bios boots from cd first

---

### Post by Shoie13 on 2007-01-18
I missed the LiveCD thing earlier, but I downloaded it and burned it to a CD, rebooted, and it still loaded to Windows. The bios have already been configured to boot from the CD first. Any suggestions?

---

### Post by Shoie13 on 2007-01-18
I have an old LIVECD version. going to download the new one and see if it helps maybe.

---

### Post by Shoie13 on 2007-01-18
No, the newest version wouldn't boot either. With the CD in the drive, it goes straight to Windows..

---

### Post by TheWizzard on 2007-01-19
take another look at your bios
EDIT: i see you can boot the ubuntu live cd. what do you see if you explore the gparted cd? does it show 1 iso file or a bunch of files?

---

