---
title: "Transfering from external hard drive to a new internal drive"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by IronSights on 2008-07-11
Last week my beloved hard drive finally passed away,
So immediately I went to everyones favorite Electronics Online Retailer, NewEgg, and purchased myself a replacement.

As for the duration of time between death of the old,
and the arrival of the new,
I installed Ubuntu on my External Harddrive to hold me off until I recieved my new drive, which just arrived today.

During this last week 've become to love Ubuntu and all it has to offer.
But now I wish to transfer all of Ubuntu onto the new drive and make it bootable.

Is this possible without having to reinstall Ubuntu on the new drive??
If so.
How?

---

### Post by logos34 on 2008-07-11
yes.

Use [Gparted]("http://gparted-livecd.tuxfamily.org/larry/move/move.htm") or [dd]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html") command (->'cloning an entire drive')

[Install grub]("http://ubuntuforums.org/showthread.php?t=224351") to the MBR of the (new) internal drive.

---

### Post by jpkotta on 2008-07-12
Yes, it's possible.  [https://help.ubuntu.com/community/Hardware/HardDisk](https://help.ubuntu.com/community/Hardware/HardDisk)

First partition the drive.  I like cfdisk, fdisk is good, I think parted is the GUI one.  Partitioning tips: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace).

Then make a filesystem on your partitions.  ext3 is the default and is very solid.  ```
mke2fs -j /dev/sd??
```  I don't know of a GUI to do that, but I'm sure they exist.

On your swap partition, format it for swap. ```
mkswap /dev/sd??
```

Once you get your filesystems set up, copy all the files over.  I think it's best to do this from a live cd, so you don't need to worry about anything changing during the copy or the virtual filesystems (/proc, /sys, ...).  Use the -a switch to cp when copying, it will preserve metadata like permissions.  I think cp is better for this than dd.

Finally, you need to update your /etc/fstab.  Ubuntu uses UUIDs these days, so you must either replace the UUIDs with device nodes (e.g. /dev/sda2) or change the UUIDs to match the new disk (see the vol_id command).

---

### Post by p_quarles on 2008-07-12
Another command (slightly faster than dd) is partimage. The Clonezilla live disk is built around this tool, and that's a relatively easy way of taking an image of one disk and cloning it to another. Also a great backup tool for the same reason.

The principal advantage of partimage over dd is that the latter clones the entire device, including empty blocks. partimage simply makes a record of those empty blocks without actually copying them. If the disk you are copying has a lot of empty space, the time saved could be noteworthy.

---

### Post by logos34 on 2008-07-12
> **p_quarles said:**
> Another command (slightly faster than dd) is partimage. The Clonezilla live disk is built around this tool, and that's a relatively easy way of taking an image of one disk and cloning it to another. Also a great backup tool for the same reason.

The principal advantage of partimage over dd is ...partimage simply makes a record of those empty blocks without actually copying them. 

yeah, I use partimage regularly to make an gzipped image of my root, and it's pretty fast on account of copying only used space.  But the problem is that you have to save the image file somewhere (to another partition or disk), then 'restore' from that (whether uncompressed or compressed)... As much as I like partimage I think it might actually take nearly as long as dd if you count the restore. (although it depends on the amount of empty space)

---

