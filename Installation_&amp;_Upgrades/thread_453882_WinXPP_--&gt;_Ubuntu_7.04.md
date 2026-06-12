---
title: "WinXPP --&gt; Ubuntu 7.04"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by Morphio on 2007-05-24
Hi, looking at actually dual booting Ubuntu with XPPro instead of just running VMWare to run Ubuntu. How do I go about installing Ubuntu without disrupting my XP installation?

---

### Post by merlinus on 2007-05-24
Run defrag and chkdsk on your windows install.  Boot from Ubuntu live cd.  When up-and-running, click the Install icon.

When you get to the partitioning scheme, you will have three or so choices.  You can allow Ubuntu to use free space, or do manual partioning.  Do not allow it to use the entire disk, or windows will be bye-bye.

It can resize your windows partition to make space.  You will need a partition for /root and /swap, and it is very useful to also create one for /home.

/swap should be equal to your RAM, unless you have less than a half gig.  Double it, in that case.

You can split the rest between /root and /home.

After installation, you will have a grub menu that will allow you to boot either OS.

Good luck!

-merlin

---

### Post by Morphio on 2007-05-24
Ok I have other hard drives, E/F (320Gb SATA disks). Should I rename the drives to say X and Y or something so the root and swap drives can be together?

I currently have...
C: Windows
E: Storage
F: Storage

Will become
C: Windows
E: Ubuntu
F: /root
G: /swap
X/Y: Storage

Does that sound right?

---

### Post by merlinus on 2007-05-24
Windows uses letters for drives.  Linux uses hda or sda for the first (or only) hard drive, hdb or sdb, etc. and sd1, etc. for partitions.

I am not familiar with installations using more than one hard disk, however.  But your scheme seems fine to me.

As long as you do not let the partitioner take over the entire disk, thereby wiping out your windows and storage drives/partitions, you should be okay.

-merlin

---

### Post by Morphio on 2007-05-24
Excellent. Thanks so much for your help! I'll report back if I encounter any problems

---

