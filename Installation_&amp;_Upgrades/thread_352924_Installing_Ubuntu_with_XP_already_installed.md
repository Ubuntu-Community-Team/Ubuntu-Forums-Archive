---
title: "Installing Ubuntu with XP already installed?"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by SnowPunk98 on 2007-02-03
I just wanted to verify that the install link you can run from the live CD will allow me to resize partitions and install Ubuntu without starting from scratch correct? Obviously I should backup my data before doing this either way but is it as simple as that?

Currently I have a 15GB Windows partition and 60GB data partition. I would like to keep the Windows partition the same, add a 5GB FAT32 partition to share files, but how big should I create the Ubuntu partition and etc. Any ideas as to how I should divide the space I have?

Also how often will the partition resizing go bad?

---

### Post by aysiu on 2007-02-03
Yes, it is as simple as that... and, yes, you should **always** back up before doing any kind of resizing.

Here's a dual boot guide for you:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

How often will it go bad? If you don't know what you're doing, I'd say about 30-40% of the time. If you know what you're doing, I'd say 0-5% of the time.

---

### Post by kodoku on 2007-02-04
Yes, it is very simple.

In the installation, manually edit the partition tables and DON'T touch the windows partition.  As for the rest of the 60 gigs, create your 5 gig FAT32, then create a swap (about the same size as your RAM, so if you have a gig of ram, format a 1 gig swap, and then create an ext3 partition for ubuntu.  The core installation of ubuntu needs 3-5 gigs, so I'd say 10 gigs for the linux partition.  If you have any free space left, feel free to add it to your FAT32 or other partitions (though having too many partitions bites into the life of the disk).

If you're not touching the windows partition, the worst thing that can happen is loss of data in the 60 gig partition.  The ubuntu installer partitioner is pretty user friendly, so unless something catastrophic (like a power outage) happens, you should be fine.

---

### Post by SnowPunk98 on 2007-02-04
Good enough, I know what I am doing so it should go well. It has been a few years since I have tried Linux since everytime I try it out I hate it and never switch over. However Ubuntu seems to have come a long way especially compared to other distros.

---

