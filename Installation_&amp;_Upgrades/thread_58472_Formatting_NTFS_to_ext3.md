---
title: "Formatting NTFS to ext3"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by Irony on 2005-08-20
I have a 38 GB primary partition currently NTFS labelled UBb (see [http://www.ironclub.net/ubuntu/part2.png](http://www.ironclub.net/ubuntu/part2.png) ). From my current fdisk -l set-up I assume this partition is hda3;

[PHP]Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2           14619       19840    41945715    7  HPFS/NTFS
/dev/hda3           19841       24792    39776940    7  HPFS/NTFS
/dev/hda4            7439       14618    57673350    5  Extended
/dev/hda5   *        7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 11.5 GB, 11525455872 bytes
255 heads, 63 sectors/track, 1401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1401    11253501    c  W95 FAT32 (LBA)[/PHP]

I would like to linux format this partition to ext3 - is this the correct format?

From reading the forums it looks like gparted or qtparted are the tools to do this, is one or the other better for this task?

Finally does this formatting mess up GRUB - should I be prepared to re-install GRUB?

---

### Post by nad on 2005-08-20
There are several filesystem types available to linux. Look at /proc/filesystems to see what types are supported on your system.

parted is a partition editor. gparted and qtparted are simply graphical frontends for parted. Other available partition editors are fdisk, cfdisk and sfdisk. parted (gparted/qtparted) however has the ability to create some types of file systems from within the program without having to exit. Otherwise, after setting a partition type, use the mkfs command with the file system of your choice to "format" the drive.

As long as this is not your /boot partition, grub should not be affected.

---

### Post by Irony on 2005-08-20
Thanks nad, it looks like GRUB should be unaffected then.

My filesystems file looks like this;

[PHP]nodev	sysfs
nodev	rootfs
nodev	bdev
nodev	proc
nodev	sockfs
nodev	pipefs
nodev	futexfs
nodev	tmpfs
nodev	eventpollfs
nodev	devpts
	ext2
	cramfs
nodev	ramfs
nodev	devfs
nodev	mqueue
	ext3
	ntfs
	vfat
nodev	usbfs[/PHP]

I assume the 5 un-nodev commented formats are supported. A quick read-up on the net and it looks like ext3 should be okay.

Once I've partitioned the drive do I need to mount it - trying to look at [http://ubuntuguide.org/](http://ubuntuguide.org/) but it seems to have been down for a few days.

---

### Post by nad on 2005-08-20
No. Make your filesystem while unmounted. Create a mount point (directory) in your current file system where you would like it attached. Then add a reference to your new filesystem in /etc/fstab that you may mount it with shortcut commands or automatically at boot up or login.

---

### Post by Irony on 2005-08-20
Thanks for that, I'll give it a go.

---

