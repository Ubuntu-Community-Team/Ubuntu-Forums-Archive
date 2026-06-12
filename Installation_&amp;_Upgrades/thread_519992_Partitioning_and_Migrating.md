---
title: "Partitioning and Migrating"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by xpnetgod on 2007-08-07
I'd love to install Ubuntu 7.04, but I can't figure out the partition part. How many partitions are needed and how should they be formated and mounted? Also, how large should these partitions be?  And can I use Partition Magic 8.0 to make, format, and size them?  BTW, are there any compatibility problems with the migration assistant?  I currently use a Dell Dimension 8200 desktop with Windows XP Professional edition and Service Pack 1 installed.

Any help will be appreciated, thanks.  :)

---

### Post by merlinus on 2007-08-07
You can use the live cd to partition.  Beforehand delete temp and other unneeded files, backup data, set virtual paging to zero (you can set it back after installing ubuntu) and defrag several times.

At the partitioning menu during install,choose to resize windows partition and use free space.  You will need one partition for root (/) and another for swap, no more than 1.5G.

If you have enough free space, you can also create a /home partition for storing data and keeping preferences and configurations intact.

-merlin

---

### Post by xpnetgod on 2007-08-10
We have already partitioned the hard drive with
Partition magic and set aside 12 gigs for the ubuntu
OS and swap partition.

On installation can the root partition be fat32?

And just what does the swap partition have
to be formatted in? Fat32 ext2 or ext3?

Thanks for any help.

---

### Post by merlinus on 2007-08-10
fat and ntfs are for windows.  Format them as ext3.

Leave 1.5G for swap, and the rest for /.

-merlin

---

### Post by xpnetgod on 2007-08-17
> **merlinus said:**
> fat and ntfs are for windows.  Format them as ext3.

Leave 1.5G for swap, and the rest for /.

-merlin

So, I make a 1.5 gig swap partition and format it as Ext3, and I make a root partition and format it as Ext3 also?  And how big should it be?  And instead of choosing it to shrink the Windows partition, can I make one on my own and use that to install Linux on?  Should ALL of these partitions be formated as Ext3?

Thanks

---

### Post by NiklasV on 2007-08-17
No, the swap partition should be formatted with the swap file system, the / partition should be formatted with ext3.

You could also let the installer decide by choosing the option to use free space on the harddrive. (though in this case, it will use 3 Gigs for swap, and that may be a bit much considering the space constraint)

To do it manually, simply choose manual partitioning and make one swap partition (choose swap as the filesystem) and one root partition (with ext3 as the filesystem)

---

