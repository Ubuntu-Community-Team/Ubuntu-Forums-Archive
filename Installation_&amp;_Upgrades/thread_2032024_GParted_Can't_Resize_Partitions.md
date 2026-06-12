---
title: "GParted Can't Resize Partitions"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by derekpock on 2012-07-22
I am trying to dual-boot a very old Windows XP with Ubuntu. I knew I would have problems changing the partitioning on the drive. XP is using ~50% of the drive space. I would like to shrink it and make another space for Ubuntu that is ~25% of hard drive. When I used the System Rescue CD ([www.sysresccd.org]("www.sysresccd.org")), I went into the normal GUI with GParted and it would not let me move SDA1 NTFS (XP). I know there is a way to do this with the command line and I know that it works. I just need instructions. :confused: Please Help

---

### Post by efflandt on 2012-07-22
Before you can shrink XP you need to disable its virtual memory (swap), reboot, and defrag it to move everything down in its partition.  But make a note of virtual memory settings, so you can set them back after resizing.

As an example when I got a computer in 2004 and tried to shrink its 200 GB drive to install 64-bit XP Pro beta and Linux (SuSE at the time), I could only shrink it about 25 GB with ntfsresize from a Linux rescue CD.  Years later when I realized that I had to temporarily get rid of the immovable virtual memory, I could have freed up over 150 GB with gparted, but did not need that much for Ubuntu.

Then shrinking the partition should go fairly quickly.  However, if you are going to "move" a partition (change where it begins), that can take a very long time (overnight), hopefully without power failure or other interruption.

---

### Post by derekpock on 2012-07-23
> **efflandt said:**
> Before you can shrink XP you need to disable its virtual memory (swap), reboot, and defrag it to move everything down in its partition.  But make a note of virtual memory settings, so you can set them back after resizing.

As an example when I got a computer in 2004 and tried to shrink its 200 GB drive to install 64-bit XP Pro beta and Linux (SuSE at the time), I could only shrink it about 25 GB with ntfsresize from a Linux rescue CD.  Years later when I realized that I had to temporarily get rid of the immovable virtual memory, I could have freed up over 150 GB with gparted, but did not need that much for Ubuntu.

Then shrinking the partition should go fairly quickly.  However, if you are going to "move" a partition (change where it begins), that can take a very long time (overnight), hopefully without power failure or other interruption.

Yes okay that might work. Could you tell me where in XP do I turn off virtual memory? Can/would it be safer to do this in safe mode. (the computer I am working on is very old and has only 256mb of RAM, this may have problems with windows if I shutdown swap/virtual memory)

I know to defrag, and I have recently done that. I can't even get one MB out of the NTFS when trying to resize. Its acting as if it is locked.

Please note I am very advanced with computers and I know almost everything about them, so don't let my "bean" rating make you think I know very little about this.

---

