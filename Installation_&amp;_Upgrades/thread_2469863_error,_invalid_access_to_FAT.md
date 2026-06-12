---
title: "error, invalid access to FAT"
date: 2021-12-11
forum: Installation &amp; Upgrades
---

### Post by openversus on 2021-12-11
Hi all,
since today my pc doesn't boot anymore and only accesses the BIOS.
I tried to insert a live USB of Ubuntu, but when I try to start the installation I get this message error (see attachment), invalid access to FAT. I just want to be able to install Ubuntu and it seems impossible.
Can someone help me?

---

### Post by oldfred on 2021-12-11
What is sdb1?

Post this:
sudo parted -l

If FAT32 partition:
sudo fsck.vfat -t -a /dev/sdb1

UEFI or BIOS system?
Installing in UEFI or BIOS boot mode?

---

### Post by openversus on 2021-12-11
Hi Fred 
here my feedback
```
lubuntu@lubuntu:~$ sudo parted -l
Model: ATA ST3000DM007-1WY1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags


Model: ASolid USB (scsi)
Disk /dev/sdb: 4028MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End     Size    Type     File system  Flags
 2      494kB  3017kB  2523kB  primary               esp


Model: WDC WDS100T2B0C-00PXH0 (nvme)
Disk /dev/nvme0n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1000GB  1000GB  ext4


Model: Unknown (unknown)
Disk /dev/zram5: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram11: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram3: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram1: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram8: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram14: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram6: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram12: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram4: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram10: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram2: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram0: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram9: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram15: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram7: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram13: 1050MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1050MB  1050MB  linux-swap(v1)
```

------------------------
```
lubuntu@lubuntu:~$ sudo fsck.vfat -t -a /dev/sdb1
fsck.fat 4.1 (2017-01-24)
Logical sector size (37008 bytes) is not a multiple of the physical sector size.
```

Last question: I think UEFI because in Aptio Setup utility in Boot Option Priorities there is UEFI HDD etc

---

### Post by oldfred on 2021-12-11
Your sdb is showing no partitions.

Since gpt does this show anything?
sudo gdisk -l /dev/sdb

You were booting from HDD not much faster NVMe drive?

---

### Post by MAFoElffen on 2021-12-12
Isn't /dev/sdb his 4GB USB Flash Drive that he has the Ubuntu LiveCD installer burned to? That he booted from? That is why is has the msdos partition table... 'ASolid' does flash/nand storage.
```

Model: ASolid USB (scsi)
Disk /dev/sdb: 4028MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End     Size    Type     File system  Flags
 2      494kB  3017kB  2523kB  primary               esp

```
Just an observation...

---

### Post by openversus on 2021-12-12
Hi I boot with a live usb Bootrepair tool. That is because if I try to boot with 
live USB Ubuntu I get the message you saw in my first post 
with sudo gdisk -l /dev/sdb I get: 
```
lubuntu@lubuntu:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 2
Using GPT and creating fresh protective MBR.
Warning! Main partition table overlaps the first partition by 34 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sdb: 7866369 sectors, 3.8 GiB
Model: USB             
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 95DE1481-DA0D-488B-ABD2-FA91FA8D536E
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1802206
Partitions will be aligned on 4-sector boundaries
Total free space is 607 sectors (303.5 KiB)
Number  Start (sector)    End (sector)  Size       Code  Name
   2             964            5891   2.4 MiB     0700  ISOHybrid
```


If I open Gparted there is only one partition /dev/nvme0n1p1 ext4 size 913.51 gb 
UEFI partition is missing
How can I restore it? Can I resolve from boot repair USB?

---

### Post by MAFoElffen on 2021-12-12
> **openversus said:**
> Hi I boot with a live usb Bootrepair tool. That is because if I try to boot with 
live USB Ubuntu I get the message you saw in my first post 
So the error message you got in your first post was NOT what your system says just trying to boot from the NVMe or HDD? That was from trying to boot from a bootable USB drive wasn't it? Because that is what that attachment in Post #1 said... That is was trying to start a LiveCD Image and failed.

I'm sorry, but oldfred, in Post#2, asked you some very important questions...
> **oldfred said:**
> What is sdb1?

Post this:
sudo parted -l

If FAT32 partition:
sudo fsck.vfat -t -a /dev/sdb1

UEFI or BIOS system?
Installing in UEFI or BIOS boot mode?
You really have not answered them... (Well half of them)

From what I can make out, and you can correct me if I am wrong... But you said your computer stopped booting (you never explained what the original problem about that was), so you tried to boot from an Ubuntu LiveCD  Installation USB. When you did, you got the error that you attached, which said you couldn't boot, because it had a bad image burned to it. Notice the failure on squashfs and the loop device error...

You seem to be able to boot from the Disk Repair LiveCD USB... But maybe not now, because in your last post, you 'changed' / tried to convert the partition table on it from MSDOS (MBR) to GPT...

Let's back up. It has an NVMe drive in it and an HDD.. So it is a fairly new computer right? We could make this easy and fast by booting from any LiveCD your can susccessfully... Say either Yann's Boot Repair Disk... Or redownload and reburn the image on the USB Flash drive you got that error from...

On whatever version, flavor or form of Ubuntu you are booted from (yann's boot Repair Disk is also Ubuntu)... DL and run the 'system-info' script in my signature line, so we can see what your computer is, how it is booting, what kind of BIOS it has (and it's capabilities), the disk layouts. etc... Please post that report to a Pastebin (that is possible in that script by answering yes when asked). That will also show all the disk info that was asked. This will be simpler and safer.

The only other questions I have, is what was installed on your computer? Is anything there of important? Or were your plans just to start over and make a fresh install? Because you did say you were trying to 'install' Ubuntu.

---

### Post by openversus on 2021-12-16
Hello, everyone,
unfortunately only yesterday I was able to analyse the problem and your posts. Fortunately you helped me to solve the problem: it was indeed a damaged Live USB and I had not considered this option, as I had previously installed Ubuntu 20.04 with the same flash drive, without problems. Now using another USB I was able to install Ubuntu.
Sorry and thanks for the help!

---

