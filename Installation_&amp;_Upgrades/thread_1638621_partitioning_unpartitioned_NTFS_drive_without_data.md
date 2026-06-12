---
title: "partitioning unpartitioned NTFS drive without data loss?t"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by admaw11 on 2010-12-05
I've got my Ubuntu Live CD, it boots up fine, trying to use Gparted to partition the drive, but it doesn't seem to want to resize the partition.

Starting to wonder if what I'm trying to acheive is actually meant to be possible. If a drive is unpartitioned, does it mean you MUST create a new partition table - meaning loose existing OS - in order to create partitions?

Completely unpartitioned drive running XP, I want to create a new partition, so I can have a dual boot with Ubuntu / XP, without loosing the existing XP installation and data on it.
Its a 20GB drive on a laptop - boots fine from CD, too old to support boot from USB.

I don't mind trying other partition software, but I'm wondering when they claim to be able to resize partitions, it might only be for partitions that have already been created - not for resizing drives with just the one unpartitioned 'partition' (meaning no partition table??).

cheers,

Adam.

---

### Post by presence1960 on 2010-12-05
You can not have an OS on an unpartitioned disk. Your disk may be one big partition, but it has to be partitioned. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Quackers on 2010-12-05
Welcome to UF :-)
If you already have XP installed then the disc is partitioned already. There may be only one partition that occupies all of the disc. To install another operating system you would need to reduce the size of the current XP partition to make space for the new operating system to occupy.
However with a disc of only 20GB Windows XP may not allow you to reduce the size of the XP partition as it may think it needs it all to run properly. Even if you could reduce the size of the partition data could still be lost.
I would suggest that the drive is not really big enough for a second operating system.

---

### Post by admaw11 on 2010-12-05
Here is the results txt file below

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4aa94aa8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,070,079    39,070,017   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4039 MB, 4039114752 bytes
37 heads, 36 sectors/track, 5922 cylinders, total 7888896 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   8     7,888,895     7,888,888   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        84E80F70E80F5FB2                       ntfs                                     
/dev/sdb1        081C-08A6                              vfat       ESTEBAN                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/ESTEBAN           vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

There is actually about 14GB free on the drive, I don't intend to really add any more to the XP installation there, this is mainly for testing the setup of a dual boot ubuntu/xp, plus it could also make the laptop usable again if ubuntu runs much faster than XP, but I don't want to loose the data that is there in the XP installation.
If successful, I'll proceed to make my netbook, and desktop multiboot with ubuntu.

---

### Post by presence1960 on 2010-12-05
With a 20 GB disk it is going to be tight. You can get away with about 8 or 9 GB for Ubuntu, But between the 2 OSs you won't have much room for storage space.

If you want to give it a whirl first back up all files you don't want to lose. Usually nothing bad will happen but you can't take the chance when performing partitioning and/or OS installations!

Then defrag windows at least once, twice is better. 

Then boot from the ubuntu CD and choose install Ubuntu. At the partitioning screen choose Install side by side )or alongside) Grab the corner of the windows partition with the mouse and slide it to the left until you have the desired space you want to allocate to ubuntu. Proceed with the install.

---

### Post by admaw11 on 2010-12-05
I've checked, and I can mount to the drive, and browse it, then unmount from it - definately not mounted then, I try resizing it in GParted, however it says Minimum Size: 19077MiB and Maximum Size 19077Mib, and any number I add in the boxes immediately goes to zero, and the bar won't let me drag to shrink either.
The drive is defragmented.

---

### Post by presence1960 on 2010-12-05
> **admaw11 said:**
> I've checked, and I can mount to the drive, and browse it, then unmount from it - definately not mounted then, I try resizing it in GParted, however it says Minimum Size: 19077MiB and Maximum Size 19077Mib, and any number I add in the boxes immediately goes to zero, and the bar won't let me drag to shrink either.
The drive is defragmented.

From gparted right click the NTFS partition and select Resize/Move. See fiest screenshot attached.

Then on the window that appears either change the numeric values or grab the right corner of the NTFS partition and resize by sliding to left. Note the double arrow cursor which is my mouse.

P.S. my double arrow cursor went away when I took the screenshot and is replaced by the traditional mouse pointer.

---

### Post by admaw11 on 2010-12-05
I've found some indication why it won't let me resize, it says there are at least 3 bad sectors on the disk and some operations may be restricted.

---

### Post by admaw11 on 2010-12-09
SOLVED by using other software to resize the NTFS partition

Then once there is unallocated space, the partitions are easily setup DURING the install process.

---

