---
title: "[SOLVED] /casper/initrd.gz"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by GrnFrag on 2008-07-22
ok, i posted this earlier, but i'm sure i put it in the wrong folder.

i have a Presario desktop, 1.9g Celeron with 512m of Ram and a 20g hdd.   Geforce4 video, linksys nic, also has onboard sound and video, but video is disabled in bios

I donwloaded both CD's for 8.04 and tried to install.   i tried to "run without changing your system", off the Live CD.  I've also tried the F6 options, and removed the "splash" and "quiet" options, as well as the 2 dashes at the end.   i tried the dashs both ways, left them there and deleted them

I always get the error above.  it's a dialog box titled "boot loader" and the message is always the same, unless i leave the dashs in the options, then i get dashs on the end of the message.

i've searched around this forum and the main site, but can't find anything.   reading sort of related posts leads me to believe that i'm not formatting my HDD correctly before install.  i started with an existing (and working) install of XP, then tried clean partitions, no partitions.   Nothing works.

HHHHEEEELLLLPPPPP!!!!!!!!

---

### Post by kellemes on 2008-07-22
> **GrnFrag said:**
> ok, i posted this earlier, but i'm sure i put it in the wrong folder.

i have a Presario desktop, 1.9g Celeron with 512m of Ram and a 20g hdd.   Geforce4 video, linksys nic, also has onboard sound and video, but video is disabled in bios

I donwloaded both CD's for 8.04 and tried to install.   i tried to "run without changing your system", off the Live CD.  I've also tried the F6 options, and removed the "splash" and "quiet" options, as well as the 2 dashes at the end.   i tried the dashs both ways, left them there and deleted them

I always get the error above.  it's a dialog box titled "boot loader" and the message is always the same, unless i leave the dashs in the options, then i get dashs on the end of the message.

i've searched around this forum and the main site, but can't find anything.   reading sort of related posts leads me to believe that i'm not formatting my HDD correctly before install.  i started with an existing (and working) install of XP, then tried clean partitions, no partitions.   Nothing works.

HHHHEEEELLLLPPPPP!!!!!!!!

Can you give us some more info on you partition scheme?
On what partition is Windows residing? etc..
As much info as possible please.

---

### Post by GrnFrag on 2008-07-22
I'm pretty open to any scheme.   At this point i'm using windows tools (fdisk) to create partitions and i dunno if that's right.   So i'm working with 1 primary 5g partition, formatted FAT16 (i figured it would be more apparent to Linux) and 15g of unpartitioned space.

edit ->  I lied, the partition is Fat32.   i'm currently formatting the rest of the disk as an extended partion with 3 logical drives inside.   one small 1g drive to be swap and 2 other 7g drives, one to be home, one to be data

---

### Post by GrnFrag on 2008-07-22
well that made the kernel load faster, but i get the same message.

just for clarity, here's my disk
20g 
1primary partition, 5g formatted Fat32
1extended partition, with 3 logical volumes
1g formatted fat32
7g formatted fat32
7g formatted fat32

---

### Post by GrnFrag on 2008-07-23
HAHA!!!  I figured it out.    My CD Burner (also reader for this box) was configured in the bios to use DMA.  switched to PIO and there she went

---

### Post by GrnFrag on 2008-07-23
HAHA!!!  I figured it out.    My CD Burner (also reader for this box) was configured in the bios to use DMA.  switched to PIO and there she went

Also had my HDD jumpered as a master when it should have been jumpered as single.   fixed that and i'm off and running.

---

