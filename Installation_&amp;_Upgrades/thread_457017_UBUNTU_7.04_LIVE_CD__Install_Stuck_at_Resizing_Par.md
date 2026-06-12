---
title: "UBUNTU 7.04 LIVE CD  Install Stuck at Resizing Partition"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by mbasam on 2007-05-28
I am trying to install 7.04 on My laptop.

I used the Guided Partitioning.
IT says: "gudied - resize SCSI3 (0,0,0), PARTITION #2 (SDA) AND USE FREED SPACE"

I clicked forward, and now for a half-hour it is on the please wait screen at 0 percent.

What should I do?

Btw: IT is partitioning 43.5 GB, and now it is 45 minutes, still at 0 percent. 120gb total hd space

Ok Problem solved, The progress was not showing, but it was progressing.

---

### Post by Pumalite on 2007-05-28
> **mbasam said:**
> I am trying to install 7.04 on My laptop.

I used the Guided Partitioning.
IT says: "gudied - resize SCSI3 (0,0,0), PARTITION #2 (SDA) AND USE FREED SPACE"

I clicked forward, and now for a half-hour it is on the please wait screen at 0 percent.

What should I do?

Btw: IT is partitioning 43.5 GB, and now it is 45 minutes, still at 0 percent. 120gb total hd space

Ok Problem solved, The progress was not showing, but it was progressing.

It's better to handle your partitions ptior to installation with Gparted. I had the same problem.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by jmore9 on 2007-05-28
I also use the boot version of gparted to partition my drives.  It will also shrink NTFS partitions with no loss of data.  Works very good almost as good a partition magic 7.0.  It is downloaded as a ISO and then you burn it to a cd.  Thenput that cd into cdrom/dvdrom and reboot and you are there
Hope this helps

---

