---
title: "I can't install Ubuntu 11.10 from CD"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by iasenko on 2011-11-24
Hello everyone, 
I don't know what I'm doing wrong but I just can't install Ubuntu 11.10. I've tried also 10.04, 10.10, 11.04, its the same problem. When the installation reaches to the partition menu, there is no hard drive in the list, and when I try pressing the install button - pops up a message : "No root file system is defined" but I can see the hard drive mounted in the home menu of the live CD,and I can browse it, open files etc. I've tried to unmount it and format the hard drive, remove the partitions from the Gparted (its 80GBs) , I've tried with different CPUs (AMD Athlon 64 x2 AM2) different MBs with Nvidia and AMD chipset and different HDDs (only 80GB available to me) also different RAM,DVD-RWs,everything...

I'll attach a pic to be more specific. If anyone have the idea what to do I'll be very thankful :)

---

### Post by BC59 on 2011-11-24
Try to format the disk from a Windows computer to the NTFS file system. I think it needs a new partition table, but I'm not sure. In any case Windows is better in such cases.

Just format it in NTFS and then while installing Ubuntu, choose Ubuntu to use all the space of the disk.

---

### Post by sudodus on 2011-11-24
Or use gparted from your installation disk to ***create a partition table*** according to the following link
[http://www.dedoimedo.com/computers/gparted.html#mozTocId555890](http://www.dedoimedo.com/computers/gparted.html#mozTocId555890)

---

### Post by Quackers on 2011-11-24
From the live cd desktop open up a terminal and copy/paste this command in to it, then copy/paste its output into your next post please.
```
sudo fdisk -lu
```

---

### Post by iasenko on 2011-11-24
I have tried also installing first Ubuntu 9.04 (which is working) and then using the same partitions. Same thing with windows XP formatted the partition in NTFS, no success. No matter if the Hard drive is partitioned or not, still nothing .. I've burned 4-5 CDs with different versions, also with AMD64.. same thing. I don't know what is going on. Quackers, I will ASAP. Thank you guys for trying to help.

---

### Post by darkod on 2011-11-24
If the disk has been used in raid before it probably has raid meta data on it. Many people wrongly think that formatting is enough to delete it, but it's not.
The ubuntu installer ignores disks with raid meta data probably to protect you installing on the wrong disk.

To make sure it's clear of meta data, boot in live mode and in terminal run:

sudo dmraid -E -r /dev/sda

If that asks you to whether you want to remove the data, this was your problem. Just confirm and that's it.

The "no root specified" error is because you are trying to install without specifying the root system partition (which you can't do since it doesn't show up the disk).

But Gparted seems to see the disk all right, so it looks like the disk is not faulty.

Give the dmraid thing a try first, and we'll take it from there.

---

### Post by iasenko on 2011-11-25
Darkod was right. All the HDDs were part of a RAID massive. Now everything works fine. Thanks a lot!!! :)

---

