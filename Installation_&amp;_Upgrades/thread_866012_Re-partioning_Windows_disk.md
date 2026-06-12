---
title: "Re-partioning Windows disk"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by Melindrea on 2008-07-21
This isn't a question about how to do it (though if you have tips not covered [here]("http://ubuntuforums.org/showthread.php?t=718351") I'm not exactly going to be unhappy, but... =), but rather what I need to save from my Linux installation to not need to redo all the things I've done?

I read something somewhere about making an installation disk from my Ubuntu - how do I do that?

And since I'm going to be repartitioning, does this sound like a fairly good setup:
/home (home folders)
/usr (applications)
swap 2GB (my memory right now is 1GB, going to be getting 2GB before Christmas)
/ 10GB
/data

And how much for /data and /usr, you think?

I have a XP installation that I'm planning on shrinking to 30gigs, which leaves about 90GB for Linux. 

Thank you,
Melindrea

---

### Post by vanadium on 2008-07-21
A fairly good setup to me would be simpler: a /, a /home and a swap. Unless you are setting up a server or have plenty of drives and space in your system, there is no need to have a separate /usr.

What you can change in your partitioning without needing to remove and recreate partitions depends on your current partitioning scheme. For example, in a situations where the / is a logical partition, one can reduce a primary windows partition, but it will not be possible to move the / into the freed space.

If you post the output of "sudo fdisk -l" here, we can see your current layout and give advice on the options.

---

### Post by Melindrea on 2008-07-21
Output from sudo fdisk -l:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12045    96751431    7  HPFS/NTFS
/dev/sda2           12046       14593    20466810    f  W95 Ext'd (LBA)
/dev/sda5           14356       14593     1911703+  82  Linux swap / Solaris
/dev/sda6           12046       14355    18555012   83  Linux

Partition table entries are not in disk order

```

I originally started the linux partition as a playground for a class, and then I started liking it more and more... So now I want to make the playground XP instead. *snickers*

---

### Post by vanadium on 2008-07-21
I will explain the output a bit:
/dev/sda1 is your Windows partition.
/dev/sda2 is an extended partition created by Windows. In that extended partition, you currently have two logical partitions, a swap partition (/dev/sda5) and your root partition (/dev/sda6).

In this scenario, it is not possible to reduce the Windows partition and move the Linux partition more to the front to use the freed space.

What can be done (without needing to reinstall) is to reduce the size of the Windows partition, then create a primary partition in the freed space, which you can format in the ext3 file system. You could use that new partition for /data, or you could even move your existing /home over there.

This action might cause your grub menu entry for Ubuntu to be broken, i.e., you may not be able to start up Ubuntu anymore. To fix that, you will need to update /boot/grub/menu.lst. (For example, "root (hd0,2)" will need to be changed to "root (hd0,3)").

---

