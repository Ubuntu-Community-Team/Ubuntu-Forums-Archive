---
title: "installer: partman doesn't see partitions of my first IDE disk"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Thares on 2007-09-12
Hello all,

I've just tried to install Ubuntu Feisty Fawn with the alternate CD-image and ran into problems at the partitioning stage.

I have two drives: hda (a IDE drive) and sda (USB drive, detected via usb-storage as SCSI), yet for some reason the partitioning program does not show partitions of the first disk - I can only erase the entire disk and make new partitions which is unacceptable.
However, partitions of the 'SCSI' drive are showing up just fine.

At first I thought this might be some ide-controller-module issue, so I've opened a console and ran 'fdisk -l /dev/hda' to see if the partitions are actually visible, if the partition table is ok, etc and everything showed up fine. I can mount the partitions without any problem.

Yet partman doesn't see them... only the entire device can be selected.
Any suggestions?

---

### Post by Pumalite on 2007-09-12
Try using Gparted and making your partitions ahead of time: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by Thares on 2007-09-12
Solved it - turns out the partition table was slightly borked, I've deleted and re-created all partitions entries, written the partition table to the disk and voila - partman recognized the partitions.

Running on Ubuntu as I'm writing this.

---

### Post by Pumalite on 2007-09-12
Good for you!

---

### Post by xintrea on 2007-09-13
> **Thares said:**
> Solved it - turns out the partition table was slightly borked, I've deleted and re-created all partitions entries, written the partition table to the disk and voila - partman recognized the partitions.

I have analogue problem, and have two quesion

1. For manipulate with partiton table you use **Gparted**?

2. After re-create partition table, you lost all data on your partitons? Or all data is untouched?

Beforehand thanks.

---

