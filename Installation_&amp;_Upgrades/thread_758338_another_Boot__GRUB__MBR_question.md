---
title: "another Boot / GRUB / MBR question"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by dig314 on 2008-04-17
My normal hard-drive has 4 partitions - 1st Win98,   2nd WinXP, 3rd and 4th no OS.

I put a 2nd Hard-Drive in, carved out a 2nd partition on it, then installed ubuntu to this 2nd partition. Then I changed the boot menu so that by default it will load XP.

2nd Hard-Drive is only temporary. When I take it out, GRUB starts to load, and fails. It can't find ubuntu, but XP will not load either.

I have seen other posts talk about MBR ( master boot record? main boot record? ). 
If I want to remove this 2nd Hard-Drive, how do I restore the MBR on my first hard-drive?

Dig

---

### Post by Pumalite on 2008-04-17
Super Grub: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by ELLORDSK on 2008-04-18
I got the same problem, Ihad W XP and installed U 8.04. I have 1 HDD with 3 Partitions Xp,U and swap.
instal went ok (I've choosen for loader the xp patition ) appart that I can't access my xp partion anymore. I try advice with supergrub.
anyway my 1st linux instalhttp://ubuntuforums.org/images/smilies/smiley-faces-75.gif
:lolflag:

---

### Post by dig314 on 2008-04-18
Thank you for the link to Super Grub. That looks very helpful.

I have a few other questions.

My main hard-drive is FAT32 with 4 partitions. I will eventually install ubuntu to one of those partitions -  or add a 5th parition as ext3.

Is it SAFE for ubuntu to read/write data to the FAT32 partitions?

Is there a safe utility to allow XP to read/write from ext3 partitions?

When I want to remove that 2nd hard-drive that currently has ubuntu installed, is there a way to reclaim the ext3 partition as fat32?

Thanks again for your help.

Dig

---

### Post by zvacet on 2008-04-18
You can read and write to windows with **ntfs-3g**.It is in synaptic and I think it is install by default.if not install it from synaptic.If you want to see Ubuntu from windows install [this.]("http://www.fs-driver.org/index.html")

---

### Post by Pumalite on 2008-04-18
Keep in mind there is a limit of 4 primary drives per HDD. Ubuntu can read&write to vfat and ntfs. From XP, you can install this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
To see, read&write Ubuntu.

---

