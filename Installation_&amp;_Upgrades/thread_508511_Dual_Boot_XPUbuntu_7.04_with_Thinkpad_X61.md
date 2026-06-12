---
title: "Dual Boot XP/Ubuntu 7.04 with Thinkpad X61"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by skier on 2007-07-24
I just picked up a Thinkpad X61.  I want to have a dual boot machine with XP and Ubuntu 7.04.  There are two partitions currently on the Thinkpad (NFTS for Windows and FAT32 for the service partition).  I don't need the service partition.  

What is the best way to do this?  I have an external optical drive and Partition Magic if I need to mod the partitions.

Thanks.

---

### Post by Pumalite on 2007-07-24
Defrg XP several times, erase all temp file. Then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to inspect and prepare your drive, shrink, expand, format partitions.

---

### Post by skier on 2007-07-24
Pumalite, thanks for the response.  I have Gparted as well.

When I blowout the service partition and create a partition for Ubuntu what should I use for a filesystem?  I tried this earlier with NFTS and when I got to install Ubuntu I didn't see the partition I created...

---

### Post by Pumalite on 2007-07-24
ext3

---

### Post by sheol on 2007-07-24
To get Ubuntu to see the partitions for installation you have to switch the hard drives into compatibility mode in the bios.  Please see the forums on the X61 to see what your getting into.

---

### Post by Pumalite on 2007-07-24
I'll save you the work: [http://ubuntuforums.org/showthread.php?t=503233&highlight=x61](http://ubuntuforums.org/showthread.php?t=503233&highlight=x61)

You probably can resolve all the issues when they come up.

---

### Post by skier on 2007-07-24
Wow.  I had to change the Bios.  Thanks!  

To be continued on the Thinkpad forum...

---

