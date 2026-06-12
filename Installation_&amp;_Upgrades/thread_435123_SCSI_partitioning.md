---
title: "SCSI partitioning"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Stormspireiv on 2007-05-06
I have a 30gb SCSI hard drive with XP loaded and a 160gb IDE for storage.  I want to resize the XP partition on my SCSI drive and load Feisty on it. I defragmented my XP drive and removed the swap file so most of the files were in the beginning. When I go to install Feisty and click manual partitioning, it gives me a very strange menu:
[IMG]http://img.photobucket.com/albums/v468/stormspire_iv/Screenshot-1.jpg[/IMG]

If I click any option, it gives me a "no root defined" error and gives me this screen.
[IMG]http://img.photobucket.com/albums/v468/stormspire_iv/Screenshot.jpg[/IMG]
It seems, for some reason, the Ubuntu installer isn't correctly identifying the partition on the SCSI drive.  Am I doing something wrong?

---

### Post by Alterios on 2007-05-06
It is reading the SCSI drives correctly, the sda and sdb names are for SCSI drives. You need to set the mount point for sda1 to /  . sda1 is the first disk and sdb1 is the second disk. When you resize and repartition make sure you create a partition for the swap file as well. (see the note at the bottom of the screen in screenshot 2).
BTW Serial ATA hard drives are shown as SCSI in Linux so if it is a newer hard drive it will show up as sdb even though it is seen as IDE in windows.

---

### Post by Stormspireiv on 2007-05-08
It won't let me resize the partition sda1.  It says "unknown" for the used space on that partition.  Though, on sdb2, it correctly identifies the used space and will allow me to resize and create a new partition from it.

---

### Post by Stormspireiv on 2007-05-08
Tried gparted. It successfully read the free space/used space on my hard drive, but said there were errors in the file system and would not resize the partition. I'm going to defrag again and run chkdsk.

---

