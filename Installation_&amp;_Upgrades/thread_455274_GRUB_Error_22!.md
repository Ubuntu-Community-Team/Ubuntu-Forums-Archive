---
title: "GRUB Error 22!"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by dc12volthippy on 2007-05-26
I recently deleted an unneeded partition(using GParted installed), then I burn the GParted Live CD, so I can make my other partition bigger again. I did this, ejected the disc, and rebooted my computer. The BIOS starts up, and then the GRUB, and it says: 

"GRUB loading stage 1.5

GRUB Loading, Please Wait...
ERROR 22"

What is this and how can I fix it?!?

---

### Post by coffeecat on 2007-05-26
From the [Grub manual]("http://www.gnu.org/software/grub/manual/"), Grub error 22:

> 22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.Sounds like the partition you deleted contained something important for the operation of Grub - such as the /boot partition with menu.lst and grub stage 2 that stage 1.5 is looking for perhaps?

If you need help rescuing this situation I suggest you post full details of your partition layout, together with what was on the now-deleted partition. Which partition has your / (root) of your in-use Linux installation? Are you multi-booting? That sort of detail.

If you haven't deleted something really critical to your in-use Linux installation, you should be able to reinstall Grub from the live CD.

**Edit**: and details of what the partition layout was like before you deleted the partition. Another possibility is that the partition with /boot now has a different device number because of the partition removal.

And there's another complication you may run into if you go about changing partition sizes. Since Edgy, Ubuntu uses UIDs in /etc/fstab rather than /dev/sda1 and suchlike. I find that a real nuisance.

---

### Post by dc12volthippy on 2007-05-26
Never mind, I"m just re-installing Ubuntu, because I don't want to go through any big hassles.

---

### Post by coffeecat on 2007-05-26
No problem. Best of luck.

---

