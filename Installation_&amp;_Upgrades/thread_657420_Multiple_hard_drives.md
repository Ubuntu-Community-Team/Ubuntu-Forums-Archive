---
title: "Multiple hard drives"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by SirShaggy on 2008-01-03
OK, starting with specs:
1 120GB IDE Hard Drive
4 160GB IDE Hard Drives

The 120GB drive is HDA and the boot drive.

I have not installed yet but wish to put /boot /swap /home and / all on the 120GB hard drive.
I also wish to mount the 4 160GB drives in the /home partition for music, videos, photos and files I save.

Should I mount them as /home/username/music for 1st drive,
/home/username/videos for the second an so on?

Is there a better way of making them all part of the /home partiton?
I dont see using exactly 160GB for music and 160GB for photos so mounting them where I 
can just add files makes more sense to me.  I am just not sure how to make my /home partition
on 5 seperate hard drives.

This system is going to be a file & print server. I am using Feisty on it so I have GUI/Desktop to
see what I am doing.

Rosewill ATX case
XClio stablepower 460W PSU
Soyo SY-KT880 motherboard
AMD Athlon XP 3200+ CPU
Zalman CNPS-7000b alcu heatsink
2x1GB OCZ EL Platinum PC3200 DDR-400 RAM
Sony 52x CDRW/DVD Combo drive
1 Samsung 120GB ATA-133 HDD
4 Samsung 160GB ATA-133 HDD's
3.5" floppy drive.


As you can see, older hardware but should be up to the task.


SirShaggy

---

### Post by logos34 on 2008-01-03
You don't need a /boot partition. 

You ought to look into LVM (Logical Volume Mgmt).  Never used it but from those specs and your criteria it seems you are a prime candidate.

---

### Post by SirShaggy on 2008-01-03
I had thought LVM was NOT intended to be used for a "SHARE" volume. As this is a server of sorts, may not be my best choice............Anyone know if this is true?


SirShaggy

---

