---
title: "Installer won't recognize already existing partition"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by kace91 on 2012-07-10
Hi, I'm having some problems installing 12.04 desktop on my asus k53sv laptop.

I have a 500gb disk which has a 150gb partition containing windows 7, which I've been using for some time. The rest of the disk should be empty space with no partitions (I left it like that some weeks ago when I installed windows, so I could install linux now).

When I try to install ubuntu from a usb stick, it boots in live mode and works perfectly, but the installer shows the disk as if it was totally empty and without partitions. 

I've had some distros installed in this disk some time ago (including ubuntu) and I've never had this kind of problem before.

I don't want to make a clean install erasing the whole disk, because I have quite a mess of data in my windows partition, so I'd rather not erase it and reinstall. What can I do?

---

### Post by oldfred on 2012-07-10
Post screenshot from gparted and/or this:

sudo fdisk -lu

does Windows need a chkdsk? Gparted/Linux will not mount and have issues with a NTFS partition that needs chkdsk to prevent damage that chkdsk may not then be able to repair.

---

### Post by kace91 on 2012-07-11
I already tried a chkdsk, but with no results.

Here they are (thanks for your help)

[IMG]http://img52.imageshack.us/img52/5893/screenshotfrom201207110.png[/IMG]


```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x87588f0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   309125119   154459136    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000090ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7855784     3927861    b  W95 FAT32
```

---

### Post by darkod on 2012-07-11
There is a warning about gpt but the partitions seem like with msdos table.

It seems this disk did have gpt table at some point, and you converted it to msdos with windows. Windows doesn't delete the backup gpt table, and linux tools get confused if the disk is msdos or gpt.

Try fixparts which should offer to remove the backup table for you. You can use it from live mode:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by kace91 on 2012-07-11
Thanks! It seems to be working now, gparted has recognized my windows partition and right now is installing with no problems so far.

---

