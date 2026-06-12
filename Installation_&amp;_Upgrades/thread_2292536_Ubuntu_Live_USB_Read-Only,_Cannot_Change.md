---
title: "Ubuntu Live USB Read-Only, Cannot Change"
date: 2015-08-28
forum: Installation &amp; Upgrades
---

### Post by dakong27 on 2015-08-28
Yesterday I created a Ubuntu Live USB with 14.04 on it to install on an old laptop of mine (to give to my kids).  I used LinuxLive USB Creator 2.9.3 on a Windows machine to create the USB.  This morning after further reading I changed my mind and wanted to put Lubuntu on the USB instead.  Trouble is that the USB is marked "read-only."  I've tried "sudo chown -R user:user /media/usb" and "sudo chmod -R 777 /media/usb" and "sudo mount -o remount,rw /media/usb" and "sudo hdparm -r0 /media/usb", but all without effect.

The USB stick itself has no physical switch for rw vs read-only.

Launching Nautilus, it shows all the files of the Ubuntu 14.04 there as read-only.  GParted, though, reports that the USB is "unallocated."

Is GParted correct?  Or is there any way to force the USB to be rw?

---

### Post by sandyd on 2015-08-28
Hi, does running 
```

sudo fdisk -l
```
in Ubuntu show the correct partitions?

If so, just unmount the partitions, and then create a new partition table using gparted or fdisk.

---

### Post by yancek on 2015-08-29
I'm not sure if I am reading your post correctly but if I do understand, you used the Linux Live USB Creator to put a Live CD of Ubuntu on a usb/flash drive intending to use it to install Ubuntu.  You now have decided you do not want to do that but want to install Lubuntu instead.  If that's what you want, use the Linux Live USB Creator to put Lubuntu on the usb/flash drive.  The system you put on the flash drive with this software will be a read-only system and you can't change that without adding persistence and if you simply want to use it to install there is really no point in that.

I'm not sure what you would want to accomplish by chaning permissions on the usb?  That won't get Lubuntu on it.

---

### Post by sudodus on 2015-08-29
If you want to start from the beginning, you can install Lubuntu with mkusb. It will overwrite the previous file system information, so there should be no problems unless you have a failing pendrive. If it is 'gridlocked' there is not much to do. See these links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by dakong27 on 2015-08-29
Thanks for the replies.  I have tried to re-do it with LinuxLive USB Creator, but Windows doesn't see the USB anymore.  My Ubuntu system does see it.  'sudo fdisk -l' returns:

> Disk /dev/mmcblk0: 64.0 GB, 64021856256 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125042688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1           32768   125042687    62504960    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2014 MB, 2014314496 bytes
255 heads, 63 sectors/track, 244 cylinders, total 3934208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a6216fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0     2060287     1030144    0  Empty
/dev/sdb2         2038760     2043303        2272   ef  EFI (FAT-12/16/32)

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb1: 1054 MB, 1054867456 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2060288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a6216fc

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           0     2060287     1030144    0  Empty
/dev/sdb1p2         2038760     2043303        2272   ef  EFI (FAT-12/16/32)



fdisk detects GPT on the USB, and says to use GParted.  GParted, though, shows the USB as unallocated.  Nautilus does show files, though.  That's the confusing part.

The outcome I am aiming for is to get Lubuntu on the USB, do the install on my old machine, then recover the USB as a regular RW drive for general use.

---

### Post by sudodus on 2015-08-29
I think you have a good chance to install Lubuntu with one of the following tools, that clone the iso file to the target pendrive. That method is independent of what was written to the pendrive before, as long as the pendrive is read-write (not read-only alias 'grid-locked').

If you can install from Ubuntu, you can use [mkusb](https://help.ubuntu.com/community/mkusb).

If you must install from Windows, you can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb).

---

