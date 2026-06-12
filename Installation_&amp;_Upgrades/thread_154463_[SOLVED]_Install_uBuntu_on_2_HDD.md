---
title: "[SOLVED] Install uBuntu on 2 HDD"
date: 2006-04-03
forum: Installation &amp; Upgrades
---

### Post by Landice on 2006-04-03
I have 2 different HDD, one is Maxtor IDE PATA, another is Seagate SATA. Now i have my Windows XP installed on the SATA drive and I've installed the uBuntu Linux on the IDE PATA drive. But when i boot up, my system straight away boot into Windows XP (I set boot from SATA in cmos), the GRUB loader didn't show up and let me choose either I wanna boot into Windows or Linux. How can I configure the GRUB Loader to show up and let me choose when my system boot up?

p/s: During installation, I've set the Linux bootable and installed the GRUB Loader on MBR...

---

### Post by Sutekh on 2006-04-04
I think that GRUB must have installed itself in the MBR of the IDE drive not the SATA one.  

Try changing the boot order so that the IDE drive is first and see if GRUB starts up.  Then see if you can boot Ubuntu and Windows XP.

---

