---
title: "How can I create a &gt;1TB partition?"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by Mondoman on 2007-09-11
I've successfully installed Feisty (and associated partitions) on my Athlon 64 x2 system's primary 30GB IDE drive.  I've also got a MegaRAID i4 controller installed, with 4x400GB drives in RAID 5, making a single roughly 1.1TB logical device as /dev/sda.  Using either GParted installed with Feisty, and the GParted Live CD, it looks like GParted can't handle partitions larger than 1TB.  With the Live CD, the device is reported with the correct "1.09 TiB" size.  Problem: when I go to create a new partition on the device (ext2 or ext3 or XFS) that takes up all the space on the device, I get the error "Could not add this operation to the list.  A partition cannot have a length of -1 sectors."  This error happens for any partition size bigger than 1TB.  Less than 1TB works fine.
What tool can I use to create a partition larger than 1TB?

---

### Post by kidders on 2007-09-12
Hi there & welcome,

People seem to have no end of problems with gparted ... I have yet to come across a "gparted is lovely" post lol. I have no idea what might be special about the 1TiB figure that causes it to fail for you. :-(

For me, basic, "no-frills" partitioners & filesystem management tools are always best ... gparted uses utilities like these anyway to configure hard disks, and they're less likely to be buggy. If I were you, I would use fdisk, cfdisk (my personal favourite), or another similar tool to create partitions, and mkfs to create filesystems in them. Hopefully, you won't run into any problems.

Imo gparted just isn't trustworthy ... if I were you I'd get rid of it. I'm sure you'll agree that manipulating terabyte filesystems is no time to be wrestling with bugs!

---

### Post by stinger30au on 2007-09-12
i suggest you tackle it from command line

---

### Post by psusi on 2007-09-12
You have to tell gparted to create a GPT disklabel instead of an msdos one, which can only handle 1 TB.

---

### Post by Mondoman on 2007-09-12
Thanks to all for the quick replies!
Being a Linux novice, I had hoped that using the GUI tools would be better at keeping me out of trouble, but since that's not the case, I'll read up on the command line tools.
BTW, the MSDOS disklabel can handle 2TB, so I'm not quite up to that problem yet.

---

