---
title: "Usb key became a necessity!"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by The Thunder Chimp on 2010-05-02
Okay so I installed Ubuntu 10.04 on my usb key this morning, not a live usb thing, a real partitioned installed. Now the partition works and all but the computer (with my computer's Ubuntu Partition, Debian Partition, and Windows 7 partition) won't boot unless the key is plugged in the port. Is there a way to get rid of this annoying handicap? Additionally, a new partition appeared in the grub(the computer grub, not the key grub), the actual partition that I created on the usb, that is.
 
Thanks for your help!

---

### Post by The Thunder Chimp on 2010-05-03
Bump

---

### Post by oldfred on 2010-05-03
You probalby installed grub into the internal drive. During normal installs grub installs where ever it wants (usually main boot drive). If you want to specify drive, there was an advanced button on screen 8 that gives you a choice of where to install.

If booted into your USB you can easily reinstall from that, or you can use a liveCD.

This reinstalls grub into the drive specified  to boot from the install (partition) you run it from:
reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub

Depending on what boot loader you were using on you internal you will have to use a liveCD or windows CD to reinstall that boot loader:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If it is windows you can install a basic boot loader to sda from Ubuntu:
Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by The Thunder Chimp on 2010-05-03
> **oldfred said:**
> You probalby installed grub into the internal drive. During normal installs grub installs where ever it wants (usually main boot drive). If you want to specify drive, there was an advanced button on screen 8 that gives you a choice of where to install.

If booted into your USB you can easily reinstall from that, or you can use a liveCD.

This reinstalls grub into the drive specified  to boot from the install (partition) you run it from:
reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub

Depending on what boot loader you were using on you internal you will have to use a liveCD or windows CD to reinstall that boot loader:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If it is windows you can install a basic boot loader to sda from Ubuntu:
Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

First of all, thanks a lot for your help :D
I tried what you asked me to do (from a live CD), and the output it gave me was the following. It seems like it does not recognize the drive:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1798fcbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       27297   217723633    7  HPFS/NTFS
/dev/sda3           27298       28649    10859940   83  Linux
/dev/sda4           28650       38913    82445518    5  Extended
/dev/sda5           38436       38913     3839503+  82  Linux swap / Solaris
/dev/sda6           28650       38031    75360852   83  Linux
/dev/sda7           38032       38435     3245098+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 32.1 GB, 32078036992 bytes
255 heads, 63 sectors/track, 3899 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1374    11035156    c  W95 FAT32 (LBA)
/dev/sdb2            1374        3900    20289536   83  Linux
ubuntu@ubuntu:~$ sudo grub-install /dev/sdb2
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sdb2
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 

Anything I could try?
Thanks again!

---

### Post by The Thunder Chimp on 2010-05-03
Wait, please don't waste your time, saving my usb key's partition, all I want is be able to boot my computer without the key. Thanks for your help.

---

### Post by oldfred on 2010-05-03
To run the first set of commands you had to be **in** your working install as the mount is where you were at in the working install. If from a liveCD you have to tell it where the grub files are at by mounting that partition.

This should be the same as the link on reinstalling grub2.

Find linux partition - if sdb1 is found:
sudo fdisk -l
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

You still can reinstall windows boot loader to sda as I previously posted.

---

### Post by The Thunder Chimp on 2010-05-04
> **oldfred said:**
> To run the first set of commands you had to be **in** your working install as the mount is where you were at in the working install. If from a liveCD you have to tell it where the grub files are at by mounting that partition.

This should be the same as the link on reinstalling grub2.

Find linux partition - if sdb1 is found:
sudo fdisk -l
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

You still can reinstall windows boot loader to sda as I previously posted.

Wait, the working install is the key or the hard-drive partition?

> **oldfred said:**
> as the mount is where you were at in the working install.

I don't understand this phrrase, sorry. Would you care to reexplain?

Thanks Again!

---

### Post by oldfred on 2010-05-04
My definition of working system was a actual working install as opposed to a liveCD or the USB equivalent of a liveCD used for installing.

Grub has to know where its files are. When installing from a working system in sdax, its knows its files are in sdax. But, if from a liveCD you mount the sdaX and tell it (make a directory & mount it) to use that partition as the location to go to for its files.

---

### Post by The Thunder Chimp on 2010-05-07
YAY!

It works! And it's all thanks to you OldFred! Thank you so much! I owe you one! You have my eternal gratitude!

                                                              =D> =D> =D> =D> =D> =D> =D>

:-D

---

### Post by oldfred on 2010-05-07
Glad you got it working.

---

