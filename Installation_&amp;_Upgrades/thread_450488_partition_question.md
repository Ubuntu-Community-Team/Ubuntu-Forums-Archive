---
title: "partition question"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by Kans on 2007-05-21
[reposting to install section]

Hi,

Still trying to install ubuntu

I started with 3 partitions (dell already did this and I dont want to remove existing partitions)
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 7 9118 73192140 7 HPFS/NTFS
/dev/sda3 9120 9725 4867 db CP/M / CTOS / ...

I used gparted to shrink my ntfs partition to 40 G, and I wanted to use the rest of the free space to install linux.
I need a dual boot system (with existing win xp & linux).

How do I go about partitioning disk? I managed to shrink the NTFS partition, now it shows 40 G in NTFS and 30 G as free space.g

First I tried to put the whole free space (30 G) into ext3 and formatted it.
Install program said it needs 2 partitions (1 root & 1 swap)

So I went back tried to create one more partition, got into cannot create more than 4 primary partitions.

How should I partition (primary/extended) and how do get around this root partition issue in install?

There seems to be already 3 primary partition, how do I get it to install without disturbing the existing partition?
I read in wikipedia there can only be 4 primary partitions / 3 primary partition and 1 extended partition?

Can I make the 30 G as extended partition and split it into two for root and swap?
Does that work?

Please help.


Thanks,
Kannan.

---

### Post by tgoose on 2007-05-21
> **Kans said:**
> [reposting to install section]
Can I make the 30 G as extended partition and split it into two for root and swap?
Does that work?


Yes, this is exactly what an extended partition is used for. If you make an extended partition then you can't directly store files on it, you have to then create logical partitons within it (one for root, one for swap and probably on for /home as well)

---

### Post by vigleik on 2007-05-21
Yes, make the rest of the space an extended partiton and then divide that up. You might or might not want a separate partition for /home. For example:

29.5GB / ext3
0.5GB swap

or

6GB / ext3
23.5GB /home ext3
0.5GB swap

Of course, exactly how big the swap partition should be depends on how much RAM you have, and how big the root partition should be if you decide to go with a separate /home partition depends on how much stuff you're planning to install.

---

### Post by Kans on 2007-05-22
Thanks for the help.
I was able to install it successfully.

Thanks,
Kans

---

