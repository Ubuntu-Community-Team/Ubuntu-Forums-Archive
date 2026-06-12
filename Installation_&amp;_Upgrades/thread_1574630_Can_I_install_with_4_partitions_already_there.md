---
title: "Can I install with 4 partitions already there?"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by Oven Glove on 2010-09-14
I'm looking to install Lucid Lynx on my (fairly new) laptop in dual boot with Win 7. But a look at the HDD from disk utility on livd cd confirmed that I already have 4 partitions in place which I believe is the maximum number of bootable partitions you can use  on a master boot record HDD. The smallest one is a 108MB FAT space called 'HP_TOOLS'; there is also a 209MB NTFS partition called 'SYSTEM', the main Windows filesystem and a 15GB recovery space,

My question is, will I be able to boot Ubuntu with 6 partitions on my drive, and what are the two smaller partitions for anyway?

Any help is appreciated.
Thanks,
Owen

---

### Post by sharathcshekhar on 2010-09-14
No. You may not. The limit is you can have 4 primary partitions, but many Extented/Logical Partitions. So if your stock Windows has taken up all the 4 primary Partitions,  I'm afraid you will have to repartition, to fit in Linux.
NOte: Linux does not need a Primary partition to boot. Windows does.

---

### Post by perspectoff on 2010-09-14
Identical question already asked, on identical equipment.

See:

[http://ubuntuforums.org/showthread.php?t=1571332](http://ubuntuforums.org/showthread.php?t=1571332)

HP has put 4 primary partitions on your hard drive. You need to convert one primary partition to an extended partition and then make sure it is big enough to install an OS. 

HP puts a utility on your computer that allows you to make recovery CDs from the data on your Recovery Partition. If you do this and successfully create the recovery CDs, then you will no longer need the Recovery Partition.

The Recovery Partition is a primary partition. It can be then deleted (using a Partition Manager such as GParted, Partition Manager (LiveCDs or for Linux) or Perfect Disk (for Windows)) and converted to "free space". The "free space" can then be used to create a New extended partition. 

Then you will have three primary partitions and one extended partition.

An extended partition can be subdivided into any number of logical partitions, and any OS (except Windows) can be installed into a logical partition (although I have seen some recent debate as to whether the Mac OSX can be installed into a logical partition).

The Recovery Partition on your hard drive is only 15 Gb, and while this is enough in which to install and run Ubuntu, if you plan to make Ubuntu a full-time OS, you might need more, eventually.

In that case, you will have to shrink the Windows partition either by using the Computer Management -> Disk Management tool from within Windows (which generally allows you to shrink the partition only about 10-20 Gb, which might be enough for you) or using Perfect Disk (paid or trial version) which allows you to resize the Windows 7 (or Vista) partition to any size you choose.

When you shrink the Windows partition, it will leave more "free space" on the hard drive. As long as the extended partition is "next to" the new free space on the hard drive, the extended partition can be expanded (or "grown") to incorporate the newly freed space. 

Partitions can be moved on the hard drive using one of the partition managers listed above (although I don't recommend moving the Windows partition), so that even if they aren't contiguous, you can move the extended partition left or right on the hard drive until it is contiguous with the free space, and then expand the extended partition in size.

Another alternative is to erase both the Recovery Partition (after creating the Recovery CDs) and the HP Tools primary partition as well. (I didn't need or like any of the HP Tools, so this was an easy choice for me, but YMMV).

That will free up two primary partitions, and Ubuntu (or any Linux OS) can successfully install using two primary partitions (one for linux-swap and one for the / root partition into which the entire OS will be installed). 

However, some resizing of these two primary partitions still needs to be accomplished. The linux-swap partition ought to be about 2 Gb (100 Mb is too small), and the Linux OS / root partition should be 15-30 Gb, as detailed above.

Once the partitions are available, the Ubuntu installer can install automatically.

---

### Post by Elfy on 2010-09-14
Have a look here [http://www.sevenforums.com/general-discussion/41178-too-many-primary-partitions.html](http://www.sevenforums.com/general-discussion/41178-too-many-primary-partitions.html)

Seems to be a lot of this about lately ... 

Once you;ve decided what you are going to do come back.

I would though suggest that if you decide to remove/create/resize any of the win partitions - use the win tool to do so. At least to create the unallocated space - you can then use that to install into.

The only other option is to install wubi - but that's not something I would normally recommend.

---

### Post by Oven Glove on 2010-09-14
Does this mean I'll have to put an extended linux partition *inside* the windows one, or will I need to erase one of the others?

---

### Post by Elfy on 2010-09-14
You will need to remove one.

Extended partitions are a type of primary - once you have the extended you can create many logicals inside it.

---

### Post by Oven Glove on 2010-09-14
Thanks everyone for your help, I now understand. One more question though; can I use a Win 7 recovery CD/DVD to fix the MBR should I feel like removing Ubuntu sometime in the future?

---

### Post by Elfy on 2010-09-15
Yes.

---

