---
title: "Wubi Install - Cannot Find Root - XP exFat Encryption?"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by MikeInDetroit on 2012-01-11
After I did the Wubi installed I had the problem below.  This is an install over a Windows XP laptop that may be encrypted.   The boot manager is Sophos (security manager) that does recognize the new entry and provides me an option to select Ubuntu.  However, after selecting Ubuntu I get the following:


Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping to a shell!
(initramfs)

There were some suggestions that the hard drive was inaccurately set in the Ubuntu .mbr and I should reset that manually.  Fair enough.  But since I am booting with Sophos and not Grub I could not use the Esc, Insert, 'e' sequence.   I did find the wubildr.mbr  and wubildr  files in the C:\  root directory but they are binary. 

I used LiveCD but could not find the hard drive (history is below).  I am not sure if this was because of the HPFS/NTFS/exFAT or because the harddrive may be encrypted. 

I did find a reference dealing with the filetype ([http://stackoverflow.com/questions/6537878/how-to-mount-a-exfat-partition-in-ubuntu-11-04](http://stackoverflow.com/questions/6537878/how-to-mount-a-exfat-partition-in-ubuntu-11-04)) but before I dig any deeper I figured I push this out there and see if there's any suggestions before I spend more time.

1. Is there a way to change the MDR file (presumably on the assumption this is the problem)?  I could copy it into another Ubuntu system if there's an editor i could use.
2. Is the encryption going to cause a problem bringing Ubuntu up at all?
3. Would I be better off deleting Wubi and going with a separate partition?  Would Sophos / encryption still be an issue?




HISTORY

Using LiveCD and trying to force a mount of /dev/sda1 gives me errors.  

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83c583c5

Device Boot Start End Blocks Id System
/dev/sda1 * 63 156296384 78148161 7 HPFS/NTFS/exFAT
root@ubuntu:~# mount -t ntfs-3g /dev/sda /media/disk -o force
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

(so I tried sda1)...

root@ubuntu:~# mount -t ntfs-3g /dev/sda1 /media/disk -o force
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@ubuntu:~# 

At this point I went on to read about HPFS/NTFS/exFAT support and the potential issue about encryption.

---

### Post by lemming465 on 2012-01-21
In general you are not going to be able to boot a WUBI install where the disk image file lives on an encrypted NTFS partition, because neither the boot loader (e.g. grub) nor the linux kernel will be able use the windows driver to decrypt the NTFS partition.

What can work in these circumstances is:
* decrypt the NTFS
* shrink the NTFS and make Linux partitions for root, swap and anything else you want in the resulting free space
* re-encrypt the NTFS
* install Linux, putting the boot loader on the Linux root (or boot, if that was separate) partition)
* install a boot manager on Windows such as EasyBCD from neosmart.net, and add your Linux partition to the Windows boot menu

---

