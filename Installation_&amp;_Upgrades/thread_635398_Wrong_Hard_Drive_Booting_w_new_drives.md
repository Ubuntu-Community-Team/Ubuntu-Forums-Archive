---
title: "Wrong Hard Drive Booting w/ new drives"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by Transition on 2007-12-08
I have Ubuntu server 6.1 running right now with a 320 gb drive running as my main drive.  The drive is /dev/sda1 and everything works great. I've installed 3 new 750gb drives (all un-formatted) and whenever i do this the OS drive (320gb)  turns into sdc1 and i can't boot?

I have the proper device boot priority set in my BIOS so the system should be loading from my 320gb drive as set.  Although for some reason when i plugin the 3 x 750gb drives my system tries to boot to sda1 which is now one of the blank 750gb drives.  Keep in mind i'm NOT moving the 320gb drive from SATA port 1 on my motherboard to another port when i plugin the other drives - so that shouldn't be effecting things.

Does anyone have any idea what's going on here?  I'm baffled..

Below is my fstab for reference...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#--------------------------------------------------------------------

LABEL=os        /               ext3    defaults,errors=remount-ro 0    1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Transition on 2007-12-09
Anyone?

---

### Post by Pumalite on 2007-12-09
What kind of drives and how did you connect them, and to what motherboard?.

---

### Post by Transition on 2007-12-09
1 x Western Digital 320gb SATA
3 x Western Digital 750gb SATA

320gb Connected to Motherboard SATA Port 1
750gb connected to 2-4 SATA Port's

---

Motherboard is DFI UT n64 Ultra-D

---

### Post by Pumalite on 2007-12-09
[http://forums.pcper.com/showthread.php?t=433524](http://forums.pcper.com/showthread.php?t=433524)

---

### Post by Transition on 2007-12-09
Are you saying that the BIOS may be corrupted?

---

### Post by Pumalite on 2007-12-09
I just found the link for you, and it looked pretty complete.

---

