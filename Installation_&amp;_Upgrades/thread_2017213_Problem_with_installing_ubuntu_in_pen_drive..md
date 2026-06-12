---
title: "Problem with installing ubuntu in pen drive."
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by Gauravs90 on 2012-07-04
I have 16 Gb pen drive in which i want to install ubuntu. but for root i want to use ext2 instead of ext4. The only problem is that GRUB fails to install on ext2.

What can I do.?

---

### Post by mastablasta on 2012-07-05
why do you want to use ext 2?
 
try to use lilo as boot loader then. maybe it supports ext2

---

### Post by sudodus on 2012-07-05
> **Gauravs90 said:**
> I have 16 Gb pen drive in which i want to install ubuntu. but for root i want to use ext2 instead of ext4. The only problem is that GRUB fails to install on ext2.

What can I do.?

Maybe this is your problem: You should not install grub to a partition but to the drive [head].

So when asked, install grub to /dev/sda (not to /dev/sda1 or /dev/sda2 ...)

---

### Post by Gauravs90 on 2012-07-05
> **sudodus said:**
> Maybe this is your problem: You should not install grub to a partition but to the drive [head].

So when asked, install grub to /dev/sda (not to /dev/sda1 or /dev/sda2 ...)

My usb drive is /dev/sdc and i'm installing grub on /dev/sdc1 which is an ext2 partition and it fails to install. i have fear that if I install on /dev/sdc it will mess with the mbr of hardisk.

Is it right to install on /dev/sdc/

---

### Post by sudodus on 2012-07-05
> **Gauravs90 said:**
> My usb drive is /dev/sdc and i'm installing grub on /dev/sdc1 which is an ext2 partition and it fails to install. i have fear that if I install on /dev/sdc it will mess with the mbr of hardisk.

Is it right to install on /dev/sdc/
The mbr of each drive 'is' /dev/sda, /dev/sdb, /dev/sdc so if you install it to ***/dev/sdc*** you won't interfere with /dev/sda.

If you do not want update-grub to add entries for the internal drive, you can disconnect your internal drives before running ```
update-grub
``` when booted from the external drive.

---

### Post by Gauravs90 on 2012-07-05
Thanks.. It worked...

---

### Post by sudodus on 2012-07-05
Congratulations :KS

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

