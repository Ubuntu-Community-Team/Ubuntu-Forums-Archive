---
title: "Grub Error 17 after 7.04 install"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by SPBesui on 2007-07-08
I installed Ubuntu 7.04 on my 5-year-old Win XP Pro box from the Live CD.  The Live CD booted fine and the Linux partition/install went silky smooth.  I'm posting this with Firefox while booted from the Live CD.

When I take the CD out and reboot, I get Grub Error 17 immediately after it checks the CD drives for bootable disks,  Nothing happens and the keyboard doesn't type anything on the screen, even though there's a blinking cursor.

Under the Live CD, I can access all partitions on both HDD's, including the XP partition and the Ubuntu partition, so I know they are not corrupted or inaccessible.

Any suggestions?  I have attached the /boot/grub/menu.lst file from the Ubuntu partition if that helps.

---

### Post by Pumalite on 2007-07-08
Check this:

[http://ubuntuforums.org/showthread.php?t=494862](http://ubuntuforums.org/showthread.php?t=494862)

---

### Post by SPBesui on 2007-07-10
OK, I followed that link and it led me to [this page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17"), which led me to [this other thread]("http://ubuntuforums.org/showthread.php?p=2995859").  I tried the recommended methods but they didn't work.

Can someone answer the question I posted in [this thread]("http://ubuntuforums.org/showthread.php?p=2995859")?  Basically, how do I access the BIOS to change the MODE to AUTO for my hdd's?

---

### Post by logos34 on 2007-07-10
> **SPBesui said:**
> Can someone answer the question I posted in [this thread]("http://ubuntuforums.org/showthread.php?p=2995859")?  Basically, how do I access the BIOS to change the MODE to AUTO for my hdd's?

you're getting warm...hit enter on CMOS, hit enter again on your ide drive channel...once there you'll have option s of LBA, auto, CHS, etc

---

### Post by SPBesui on 2007-07-14
I got to the screen with the option to change the Access mode, but both hard drives were already on AUTO.

Any other suggestions?

---

