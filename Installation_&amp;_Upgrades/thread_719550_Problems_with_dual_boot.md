---
title: "Problems with dual boot"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by planemanx15 on 2008-03-09
Ok so i got into the Ubuntu scene last week after getting tired of Vista, and i installed ubuntu 7.10 on 110gb hdd. Ubuntu has 90gb and i left 20gb untouched... I then installed XP on that leftover 20gb for my flight simulator game and my zune software.  After installing windows my GRUB loader screen isn't appearing and the computer logs directly into windows. My question is how do i get either the windows O\S selection screen or the GRUB screen back?  Im very new to this and have a lot of knowlege in Windows but not much is linux. Thanks for all your help!

---

### Post by 1010011010 on 2008-03-09
Windows wants to  be the only OS.  It wrote over the MBR.  You can try super grub  [Super Grub]("http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml) to reinstall grub.

Just for future reference... install Windows and then Linux.

---

### Post by Bruce M. on 2008-03-09
> **planemanx15 said:**
> Ok so i got into the Ubuntu scene last week after getting tired of Vista, and i installed ubuntu 7.10 on 110gb hdd. Ubuntu has 90gb and i left 20gb untouched... I then installed XP on that leftover 20gb for my flight simulator game and my zune software.  After installing windows my GRUB loader screen isn't appearing and the computer logs directly into windows. My question is how do i get either the windows O\S selection screen or the GRUB screen back?  Im very new to this and have a lot of knowlege in Windows but not much is linux. Thanks for all your help!

Your problem is you installed Windows AFTER Ubuntu, that destroyed GRUB because it overwrote the MBR.

Take a look at this [HowTo Restore Grub]("http://ubuntuforums.org/archive/index.php/t-24113.html")

Hope that helps.
Bruce

---

