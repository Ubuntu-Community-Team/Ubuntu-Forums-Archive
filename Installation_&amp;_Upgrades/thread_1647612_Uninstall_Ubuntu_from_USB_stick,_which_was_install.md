---
title: "Uninstall Ubuntu from USB stick, which was installed with Universal USB Installer"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by Seekmo on 2010-12-17
Mmm the title has too many times the word "install" :P

Anyway, I installed Ubuntu 10.10 in an USB stick and now i want to erase it. But when i try to delete it, a sign says it's protected and cannot by modified.


How do I erase it?



PD: Sory if this is the wrong section.

---

### Post by sanderj on 2010-12-17
Boot any operating system (but NOT from the USB stick), then put in the USB stick, and delete all contents.

---

### Post by gt3pilot on 2010-12-17
Or just format it...

Kirk

---

### Post by Seekmo on 2010-12-22
The problem is... AS I SAID... i can't erase any file. They're protected.


Ok i should format then.... but how? That's what i'm asking

---

### Post by C.S.Cameron on 2010-12-22
If your flash drive has only one partition it is safe to format in Windows.
Plug it in, open Explorer right click the drive and hit Format.
If it has more than one partition boot the Live CD and use System/Administration/Gparted Partition Editor to delete partitions and then create a new one with FAT32 format.

---

### Post by wiltgen on 2013-02-02
Can't format or even mount the USB drive because it complains being a READ ONLY file system.

GPARTED can't do the job... actually does all it supposed to do "on memory" but when I ask to write in the disk it revert the changes.

---

### Post by howefield on 2013-02-02
Old thread closed.

---

### Post by Old_Grey_Wolf on 2013-02-02
> **wiltgen said:**
> Can't format or even mount the USB drive because it complains being a READ ONLY file system.

GPARTED can't do the job... actually does all it supposed to do "on memory" but when I ask to write in the disk it revert the changes.

Please start your own thread. Provide more information. What you provided here is not enough information for someone to guess what your problem is. Describe the symptoms in more detail.

---

