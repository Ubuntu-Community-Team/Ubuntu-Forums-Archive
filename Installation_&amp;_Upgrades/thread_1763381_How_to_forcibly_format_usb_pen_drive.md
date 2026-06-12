---
title: "How to forcibly format usb pen drive?"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by scott_tiger on 2011-05-20
I have a 4 GB usb pen drive, but I am unable to format it.

Even if I delete some files and eject it , I am getting back the same files again?

Guide me any cmds or any software to forcibly format my pen drive?

---

### Post by dabl on 2011-05-20
One possibility is that the memory on that drive is failing.

Assuming that it is just a corrupted filesystem (mainly caused by yanking the drive out without using "safely remove"), you can start over with a new partition table, and then format the drive to a FAT32 filesystem.

Use GParted, browse to the drive, first choose "Device > New Partition Table" and then "Apply".  Then you might have to browse to the device again, highlight the "unallocated space" graphic, and right-click and "New" filesystem and choose FAT32 from the menu.

Don't make a mistake when you choose the drive in GParted -- this command will nuke everything on the drive that you choose.

---

### Post by memilanuk on 2011-05-20
I've got a similar problem... a relatively new (less than six months old) 2GB usb pen drive that I couldn't format in Ubuntu - kept getting i/o errors.  Stuck it in a Windows machine, same thing.  Most likely... drive is just hosed and best off pitching it in the trash.

---

### Post by jerrrys on 2011-05-20
as said gparted or disk utility should do the job

---

