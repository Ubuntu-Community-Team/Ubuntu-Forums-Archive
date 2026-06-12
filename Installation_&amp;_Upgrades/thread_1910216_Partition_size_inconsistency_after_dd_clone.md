---
title: "Partition size inconsistency after dd clone"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by ottadini on 2012-01-16
We have recently upgraded a system HDD - it was 160GB, now 2TB. We upgraded as we were running low on space, mainly on /usr, and also on /home.

I prepared the new drive with a Live CD and GParted. Then I cloned using dd /, /usr, and /boot to the new drive. The partition size of /usr on the old drive *was* 23GB, but I made it ~50GB on the new larger drive. However it seems there is now an inconsistency between what parted sees, and what fdisk etc see. All of the partition sizes are inconsistent, I suppose due to the difference between GiB and GB, but /usr is way off, and /boot is as well. Is /? I can't quite tell. sda7 is 14G to df, but 15.2GB to parted.

Here's df -h:
```
harb@joan:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda7              14G  2.0G   12G  16% /
none                   12G  308K   12G   1% /dev
none                   12G  400K   12G   1% /dev/shm
none                   12G  456K   12G   1% /var/run
none                   12G     0   12G   0% /var/lock
none                   12G     0   12G   0% /lib/init/rw
/dev/sda6             5.8G  140M  5.4G   3% /tmp
/dev/sda1             230M   55M  164M  25% /boot
/dev/sda9              37G  176M   35G   1% /scratch
/dev/sda10            1.7T  185G  1.4T  12% /home
/dev/sda5              23G   21G  992M  96% /usr
```

Here's a snapshot of the partitions from parted:
```
harb@joan:~$ sudo parted /dev/sda print
[sudo] password for harb: 
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  263MB   263MB   primary   ext4            boot
 2      263MB   2000GB  2000GB  extended
 5      263MB   52.7GB  52.4GB  logical   ext4
 6      52.7GB  59.0GB  6292MB  logical   ext4
 7      59.0GB  74.2GB  15.2GB  logical   ext4
 8      74.2GB  148GB   73.4GB  logical   linux-swap(v1)
 9      148GB   190GB   41.9GB  logical   ext4
10      190GB   2000GB  1811GB  logical   ext4
```

Here's fdisk:
```
harb@joan:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001db18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      257008+  83  Linux
/dev/sda2              33      243201  1953254992+   5  Extended
/dev/sda5              33        6406    51199123+  83  Linux
/dev/sda6            6407        7171     6144831   83  Linux
/dev/sda7            7172        9019    14844028+  83  Linux
/dev/sda8            9020       17943    71681998+  82  Linux swap / Solaris
/dev/sda9           17944       23042    40957686   83  Linux
/dev/sda10          23043      243201  1768427136   83  Linux
```

---

### Post by oldfred on 2012-01-16
I try to avoid dd if I can.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

dd is intended to copy from same size to same size. I think you have the larger 50GB partition size in the partition table, so fdisk sees the larger size, but dd copied the entire partition as 23GB and parted sees the new start & end and thinks it is 23GB.

Are you gonig to keep old drive mounted? As UUIDs will also be the same as dd also copied the internal structure.

Also with new large drives many are formated to gpt, but dd can damage a gpt drive as it is so different in partition structure.
Do not use dd to copy drive with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)

---

### Post by ottadini on 2012-01-16
Thanks oldfred. Bit late for that advice for me - I'm of the opinion that the problem is soluble without starting again. However, thanks for the info on dcfldd, I might try that next time. I think in future I'll just use dd (or dcfldd) to clone the boot sector for each partition, and then use rsync for the files. 

For a bit more info: I created the partitions first, then used dd to clone individual partitions. Then, I cloned the disk's MBR from the old drive to the new drive (the first 446 bytes, being careful not to overwrite the partition table). My dd commands were like this:

```
dd if=/dev/sdb1 of=/dev/sda1 conv=notrunc,noerror
```

> dd is intended to copy from same size to same size. I think you have the larger 50GB partition size in the partition table, so fdisk sees the larger size, but dd copied the entire partition as 23GB and parted sees the new start & end and thinks it is 23GB.
Other way around: parted sees the 'correct' size, fdisk the old drive's size. 

I have removed the old drive from the system, definitely not the issue :)

How do I tell if the new drive has a gpt? 
The new drive works - I'm using it now to type this. It just reports the incorrect size via fdisk, df, and possibly others.

---

### Post by oldfred on 2012-01-17
Unless you specifically told gparted or parted to use gpt as the partitioning it will be MBR. But new clean installs of Ubuntu to empty drives over some size above 1TB will automatically be set to gpt. I have several smaller drives and a flash drive with gpt.

```
fred@fred-LT-A105:~$ sudo parted /dev/sdb unit s print
[sudo] password for fred: 
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 31375360s
Sector size (logical/physical): 512B/512B
[COLOR=Red]Partition Table: gpt[/COLOR]

Number  Start      End        Size       File system  Name          Flags
 1      2048s      4095s      2048s                   KingstonData  bios_grub
 2      4096s      14749695s  14745600s  ext4
 3      14749696s  29327359s  14577664s  ext4
 4      29327360s  31373311s  2045952s   ntfs

```

I thought fdisk read partition table.

What does sfdisk show and I would backup a copy before trying fixes. And is sfdisk what you consider to be the correct version?

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by ottadini on 2012-01-17
Hi hi,

```
root@joan:/home/harb# parted /dev/sda unit s print
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End          Size         Type      File system     Flags
 1      63s         514079s      514017s      primary   ext4            boot
 2      514080s     3907024064s  3906509985s  extended
 5      514143s     102912389s   102398247s   logical   ext4
 6      102912453s  115202114s   12289662s    logical   ext4
 7      115202178s  144890234s   29688057s    logical   ext4
 8      144890298s  288254294s   143363997s   logical   linux-swap(v1)
 9      288254358s  370169729s   81915372s    logical   ext4
10      370169793s  3907024064s  3536854272s  logical   ext4
```

So it's msdos partition table.

Yes I believe in the numbers sfdisk reports, here they are:

```
root@joan:/home/harb# sfdisk -l /dev/sda

Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+     31      32-    257008+  83  Linux
/dev/sda2         32  243200  243169  1953254992+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5         32+   6405    6374-  51199123+  83  Linux
/dev/sda6       6406+   7170     765-   6144831   83  Linux
/dev/sda7       7171+   9018    1848-  14844028+  83  Linux
/dev/sda8       9019+  17942    8924-  71681998+  82  Linux swap / Solaris
/dev/sda9      17943+  23041    5099-  40957686   83  Linux
/dev/sda10     23042+ 243200  220159- 1768427136   83  Linux
```

---

### Post by ottadini on 2012-01-17
What does this mean? I have hidden sectors and a Host Protected Area... ?


```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 2000 GB / 1863 GiB - ATA WDC WD20EARS-00M

Hidden sectors are present.

size       3907029168 sectors
user_max   3907029168 sectors
native_max 18446744073321613488 sectors
dco        18446744073321613488 sectors
Host Protected Area (HPA) present.





[ Continue ]  Continue even if there are hidden data

```

---

### Post by ottadini on 2012-01-17
Thirdly... I keep finding out weird things I never knew about...

It seems that when I changed disks, the UUID of the swap partition changed. I realised this, and thought I knew what I was doing when I simply updated /etc/fstab. However, I had never heard about /etc/initramfs-tools/conf.d/resume. So, they now report different UUIDs for swap:
```
Swap UUID reported by blkid   a98a0cca-eebc-492b-88a6-d492550e2615
Swap UUID in fstab            a98a0cca-eebc-492b-88a6-d492550e2615
harb@joan:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=3bb5db30-965d-4955-8f79-3d01036b8a49
```

I plan on changing the UUID of the (new drive's) swap partition to the one reported by /etc/initramfs-tools/conf.d/resume. Here's how I think I need to do it, can someone do a sanity check for me? I got these commands from a Mandriva forum:
```
sudo su
swapoff -a
mkswap -U 3bb5db30-965d-4955-8f79-3d01036b8a49 /dev/sda5
swapon -U 3bb5db30-965d-4955-8f79-3d01036b8a49
```

---

### Post by ottadini on 2012-01-17
that should be sda8

---

### Post by oldfred on 2012-01-18
that is a new one for me.

Grub also saves the drive to reinstall to on grub updates. It is the hardware definition of the drive.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

This all just adds to why I normally suggest a new clean install which also then eliminates all the old cruft like logs, history etc. The reconfiguration and repair takes longer than a new install and copy /home back.

Not sure what HPA is. I do know that BIOS settings are often copied to drive.

Linux ext4 normally reserves 5% on hard drive to prevent system from running out of space.

---

### Post by ottadini on 2012-01-18
Thanks again oldfred, this is getting stranger. 

```
harb@joan:~$ sudo debconf-show grub-pc 
...
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD1600AAJS-75M0A0_WD-WMAV3H405181
...
```
and

```
harb@joan:~$ ls /dev/disk/by-id/
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887-part1
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887-part10
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887-part2
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887-part5
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887-part6
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887-part7
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887-part8
ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5876887-part9
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887-part1
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887-part10
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887-part2
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887-part5
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887-part6
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887-part7
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887-part8
scsi-SATA_WDC_WD20EARS-00_WD-WCAZA5876887-part9
wwn-0x50014ee205b367e9
wwn-0x50014ee205b367e9-part1
wwn-0x50014ee205b367e9-part10
wwn-0x50014ee205b367e9-part2
wwn-0x50014ee205b367e9-part5
wwn-0x50014ee205b367e9-part6
wwn-0x50014ee205b367e9-part7
wwn-0x50014ee205b367e9-part8
wwn-0x50014ee205b367e9-part9
```
so grub at least needs updating somehow to look at the new disk. Is this possible?

---

### Post by oldfred on 2012-01-18
Sorry, thought I posted it.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Check again afterwards to be sure. 

I see my drive shows all partitions 3 times each as ata, scsi, & wwn also.

---

