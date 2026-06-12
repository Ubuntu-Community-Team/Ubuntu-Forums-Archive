---
title: "Unallocated drive after installing windows"
date: 2018-12-20
forum: Installation &amp; Upgrades
---

### Post by guitarguy999 on 2018-12-20
So i installed windows 10 over ubuntu 18 on my primary drive. now windows is showing my 2tb drive as unallocated.  I loaded up ubuntu on a usb stick, and ubuntu is showing is also as unallocated, and windows reserved. can someone please tell me what has happened?

---

### Post by yancek on 2018-12-20
You are not being clear on your situation.  What I read is that you installed windows 10 onto a drive on which you previously had Ubuntu thus overwriting completely the Ubuntu install.  What do you expect to see on the 2TB drive?  What was on it previously, a data partition of what filesystem type?  Was it used solely for windows or for Ubuntu or for both?  Maybe some more details as well as answers to these questions would help.  Try booting the Ubuntu usb and from a terminal run each of the commands below consecutively, hit the Enter key after each and post the output here.

> sudo parted -l
sudo fdisk -l
df -h

THe first two commands, that is a Lower Case Letter L in the command.

---

### Post by guitarguy999 on 2018-12-20
yes, I installed windows 10 over ubuntu completely, and I was expecting to see my backup data from the 2tb drive.  Prior to this install I was using only ubuntu, and I honestly cant remember which filesystem type I was using for the 2tb backup drive.  find and mount found nothing, and right now im running MiniTool partition recovery

---

### Post by guitarguy999 on 2018-12-20
here is a picture of the current status

---

### Post by guitarguy999 on 2018-12-20
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST2000LM015-2E81 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

```
Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  16.8MB  16.8MB               Microsoft reserved partition  msftres


Model: ATA WDC WDS500G2B0B- (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  538MB  537MB   fat32        EFI System Partition          boot, esp
 2      538MB   555MB  16.8MB               Microsoft reserved partition  msftres
 3      555MB   108GB  107GB   ntfs         Basic data partition          msftdata
 4      108GB   215GB  107GB   ntfs         Basic data partition          msftdata
 5      215GB   323GB  107GB   ntfs         Basic data partition          msftdata
 6      323GB   430GB  107GB   ntfs         Basic data partition          msftdata


Model: SanDisk Ultra Fit (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  124GB  124GB  primary  fat32        boot, lba
```






```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 264B9BFD-C099-4A08-AABC-BC245936E70C

Device     Start   End Sectors Size Type
/dev/sda1     34 32767   32734  16M Microsoft reserved

Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: EC9911D4-CF07-4864-BB6D-3F3E831CF15F

Device         Start       End   Sectors  Size Type
/dev/sdb1       2048   1050623   1048576  512M EFI System
/dev/sdb2    1050624   1083391     32768   16M Microsoft reserved
/dev/sdb3    1083392 210798591 209715200  100G Microsoft basic data
/dev/sdb4  210798592 420513791 209715200  100G Microsoft basic data
/dev/sdb5  420513792 630228991 209715200  100G Microsoft basic data
/dev/sdb6  630228992 839944191 209715200  100G Microsoft basic data


Disk /dev/sdc: 115.7 GiB, 124218507264 bytes, 242614272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x01015ddd

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdc1  *     2048 242614271 242612224 115.7G  c W95 FAT32 (LBA)
```







```
ubuntu@ubuntu:~$ df -h 
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           787M  1.7M  786M   1% /run
/dev/sdc1       116G  1.9G  114G   2% /cdrom
/dev/loop0      1.8G  1.8G     0 100% /rofs[[IMG]https://ubuntuforums.org/attachment.php?attachmentid=281980&stc=1&thumb=1&d=1545352425[/IMG]]("https://ubuntuforums.org/attachment.php?attachmentid=281980&d=1545352425")    				
/cow            3.9G  410M  3.5G  11% /
tmpfs           3.9G   28M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs           3.9G  516K  3.9G   1% /tmp
tmpfs           787M   64K  787M   1% /run/user/999
/dev/loop1       87M   87M     0 100% /snap/core/4917
/dev/loop2       35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop3      141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop4      2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop5       13M   13M     0 100% /snap/gnome-characters/103
/dev/loop6       15M   15M     0 100% /snap/gnome-logs/37
/dev/loop7      3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
ubuntu@ubuntu:~$
```

---

### Post by yancek on 2018-12-20
The output you posted only shows a windows partition of 16MB in size.  I expect you will need to use some recovery software to find any data on that drive.  If you don't have success with the software you are now using, you might try testdisk to recover.

---

### Post by guitarguy999 on 2018-12-21
here is a screenshot of a completed scan.

i see "my backup".

i really dont understand all these other file systems especially the NTFS that has a used size of 162.92gb.

i think i will clone the drive before doing anything at all.

can someone please explain to me how that math adds up. i see a 1.82TB drive (disk 1, GPT), then it says 346gb unallocated, then 346.1gb used then 237.9gb unallocated, then  my backup (ext4) 1838GB.

The 1838GB with 45% being used and also being ext4 looks exactly like what i lost

---

