---
title: "[Two drives] Is this partitioning scheme possible?"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by navneeth on 2006-10-30
My computer has two separate drives. The Master(20 GB) contains Windows C:, D: and E, while the second (Slave 40GB) contains Dapper and F(Windows). I want to do a  fresh install of Edgy in the second drive, but this time making space to share some files between the OS's, and also the \home partition. Can I create all three in the second drive?

Here are a couple more questions:

Can I make these partitions using Gparted live CD and then install Ubuntu using the alternate CD (letting it install in the free space)?

If I can do the above, how do I actually create these partitions, i.e., How do I make sure that Linux recognises them, especially the shared folder - what do I name it?

Thanks for any help. :)

---

### Post by Archmage on 2006-10-30
> **navneeth said:**
> If I can do the above, how do I actually create these partitions, i.e., How do I make sure that Linux recognises them, especially the shared folder - what do I name it?

In the process of the partition you can give them all the nessacary mount point. (eg. \ for your dapper install and \home for your home-partition.)

BTW: Don't forget to make a \swap-partition.

The problem is your partition for trading. You could either use as a filesystem fat32 (no files over 2 GB) or use ext3 (with an additional driver in Windows - it might damage your data) or NTFS (with an ntfs-3g in Ubuntu - it might damage your data).

---

### Post by blind0wl on 2006-10-30
If I was you, Id make your shared partition Fat32, which Linux will be able to read/write to and will obviously be seen in Windows.  GParted should be able to create these for you.  If not, grab fdisk and create the fat32 partitions after install.

Cheers

Blindy

---

### Post by navneeth on 2006-10-30
Thanks, guys! So it won't matter if the shared folder and Windows are in different drives? I ask this because most pages I see talk about only comps. with a single hard disk.

> In the process of the partition you can give them all the nessacary mount point. (eg. \ for your dapper install and \home for your home-partition.)

What about the shared folder? I don't need to name it in any particular way, right?

> 
BTW: Don't forget to make a \swap-partition.

When I installed Dapper, I let it use the max. free space and it created a swap automtically. I hope to the same this time.

---

