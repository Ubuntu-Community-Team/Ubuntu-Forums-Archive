---
title: "More Installation Problems!"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by antex on 2007-03-31
In trying to get Ubuntu and GRUB installed without affecting the MBR of the drive, I chose the location of GRUB to be /dev/hda5, since i have hda1, hda2, hda3, and hda4 is an extended partition, and hda5 is the ext3 partition, and hda6 is the partition formatted as linux swap.

(Note: (hd0,6) did not work as a location for GRUB - it gave me an error executing grub-install (hd0,6))

After installing Ubuntu, I rebooted the computer -- after checking that hda5 had the boot flag -- and then nothing happened; I just had a blinking underscore, with no error message or anything.

---

### Post by zvacet on 2007-04-01
[http://ubuntuforums.org/showthread.php?t=56723&highlight=mbr]("http://ubuntuforums.org/showthread.php?t=56723&highlight=mbr")

---

