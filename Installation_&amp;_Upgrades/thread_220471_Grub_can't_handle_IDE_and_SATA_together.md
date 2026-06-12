---
title: "Grub can't handle IDE and SATA together"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by wyo on 2006-07-21
After I upgraded my Linux kernel package the Grub "menu.lst" file was changed obviously. Unfortunatly this reminded me of an old problem I already outlined in [http://www.ubuntuforums.org/showthread.php?t=181621]("http://www.ubuntuforums.org/showthread.php?t=181621"). If a SATA and an IDE drive is installed Grub always numbers the IDE drive as (hd0,?) and the SATA drive as (hd1,?) even if it's the other way around. After this upgrade I again had to change

   **root (hd1,2)**

to

   **root (hd0,2)**

so my to /dev/hda2 installed system boots. Luckally I have a dualboot Windows with the ext2 driver so I can edit it easly. Sounds funny that the best way to fix such a broken Linux is using Windows.

O. Wyss

---

### Post by Herman on 2006-07-22
> Sounds funny that the best way to fix such a broken Linux is using Windows. You could also have accessed your Ubuntu's /boot/grub/menu.lst file by mounting your hard disk installed Ubuntu with the Ubuntu Dapper 'Desktop' Live/Install CD (or any Live CD), in the following manner, [Click Here]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").

> [http://www.ubuntuforums.org/showthread.php?t=181621](http://www.ubuntuforums.org/showthread.php?t=181621). If a SATA and an IDE drive is installed Grub always numbers the IDE drive as (hd0,?) and the SATA drive as (hd1,?) even if it's the other way around. Thanks for posting that great link, I found that interesting. That helps to explain some things I've been wondering about. I'd be interested to learn a little more about this subject. This still happens all the time when people mix ide and sata drives.
Here's what the Grub manual has to say about this, [15.3 The map between BIOS drives and OS devices]("http://orgs.man.ac.uk/documentation/grub/grub_15.html#SEC113")  
That seems to me to read that maybe we should be editing our device.map files in addition to our menu.lst files. ..Or am I misunderstanding this? Anyone agree? Disagree? :confused:
I don't have any computer yet with more than one hard disk or with mixed IDE and SATA to find out for myself, but I'd still like to know.

---

### Post by wyo on 2006-07-23
> **Herman said:**
> ... 'Desktop' Live/Install CD (or any Live CD), ...

True, albeit there are two reasons against it.

1. The install with a live CD overwrites the MDB without confirmation even in a multiboot environment which is one of the most stupied mistakes an install disk can do. Therefore the Ubunto live CD is IMO considered completely broke.

2. Mounting and fixing something on the hard disk is rather complicated in the resuce mode (text mode install CD). The resuce mode needs quite some improvments until it's usable. Anybody using a multiboot Windows with the ext2 driver is much more convenient.

> **Herman said:**
> ... but I'd still like to know.

IMO the best thing to inprove the situation is to get rid of the special numbering scheme in Grub and _always_ use the "/dev/..." notation", then there wouldn't be any mismatch possible.

O. Wyss

---

