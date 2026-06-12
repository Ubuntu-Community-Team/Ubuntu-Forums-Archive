---
title: "Dual boot Ubuntu and Windows"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by zooounds on 2007-03-26
I have Ubuntu edgy currently installed.

I have two disks hda and hdc in a raid1 array for this. hdb is the cd-rom and hdd is my storage disk. The first partition on hdd is for windows.

Is it possible to install on this space? Even as hdd is slave?

If I install Windows XP SP2, will inte in any way harm GRUB located on hda and hdc? Or any other data on these disks?

After installing,  I can use GRUB on these two disks to load Windows from hdd, right?

---

### Post by lha on 2007-03-27
> **zooounds said:**
> I have Ubuntu edgy currently installed.

I have two disks hda and hdc in a raid1 array for this. hdb is the cd-rom and hdd is my storage disk. The first partition on hdd is for windows.

Is it possible to install on this space? Even as hdd is slave?

If I install Windows XP SP2, will inte in any way harm GRUB located on hda and hdc? Or any other data on these disks?

After installing,  I can use GRUB on these two disks to load Windows from hdd, right?

It is possible have Windows on hdd, but I'm not sure if you can install it directly there. Atleast the older Windows' were very picky with the install partition. Unplug hda and hdc before you install Windows to save Ubuntu and grub. I'm not familiar with the Windows XP installer, so I do not know if you have to make hdd a master or not. After installing Windows, plug your hd's like they were in the beginning and search the forums for instructions on how to boot Windows from a disk that is not hda. (In short, adding map (hd0) (hd3) and map (hd3) (hd0) to grub in addition to the usual chainloader-stuff does the trick.)

---

