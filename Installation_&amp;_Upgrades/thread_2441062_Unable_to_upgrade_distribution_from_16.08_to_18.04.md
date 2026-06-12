---
title: "Unable to upgrade distribution from 16.08 to 18.04 due to insufficient room in /boot"
date: 2020-04-18
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2020-04-18
My /boot partition is only 255 MB, so I can't upgrade to 18.04.  Is there any way to make to /boot partition larger, or do I have to do a clean install? 

Useful information:
```
>ls -l /boot
-rw-r--r-- 1 root root  1251054 May  2  2018 abi-4.4.0-124-generic
-rw-r--r-- 1 root root   190654 May  2  2018 config-4.4.0-124-generic
drwxr-xr-x 5 root root     1024 Nov 14 21:05 grub
-rw-r--r-- 1 root root 40141398 Feb  5 12:50 initrd.img-4.4.0-124-generic
drwx------ 2 root root    12288 Aug  5  2015 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root      255 May  2  2018 retpoline-4.4.0-124-generic
-rw------- 1 root root  3898100 May  2  2018 System.map-4.4.0-124-generic
-rw------- 1 root root  7143952 May  2  2018 vmlinuz-4.4.0-124-generic
```

```
sudo parted -l
Model: ATA INTEL SSDSC2CT24 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   240GB  240GB  extended
 5      257MB   240GB  240GB  logical                lvm


Model: ATA SanDisk SDSSDHP0 (scsi)
Disk /dev/sdb: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   64.0GB  63.8GB  extended
 5      257MB   64.0GB  63.8GB  logical                lvm


Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB


Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 206GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  206GB  206GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-swap_1: 34.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  34.0GB  34.0GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 34.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  34.0GB  34.0GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 29.7GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  29.7GB  29.7GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md0: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4

```
I booted from /dev/sdb.

---

### Post by mörgæs on 2020-04-18
Have you considered skipping 18.04 and doing a clean install of 20.04 in a week or two?

---

### Post by dipol0 on 2020-04-18
> **asb3 said:**
> My /boot partition is only 255 MB, so I can't  upgrade to 18.04.  Is there any way to make to /boot partition larger,  or do I have to do a clean install? 

sudo parted -l

Model: ATA SanDisk SDSSDHP0 (scsi)
Disk /dev/sdb: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   64.0GB  63.8GB  extended
 5      257MB   64.0GB  63.8GB  logical                lvm

I booted from /dev/sdb.

Sorry for my ENG :)

Boot from LiveCD/USB (Ubuntu 18.04 / PartedMagic) and use GParted for resize /boot partiton on /dev/sdb ??? !!! Be carefully!!! Strongly recommended have a full backup you /dev/sdb before made experiments ;)

---

### Post by asb3 on 2020-04-19
Yes.  If I have to do a clean install, I'll install wait a week and install 20.04.

---

### Post by lvm on 2020-04-19
Resizing partitions is possible, the very first google search result points to a gparted tutorial [https://www.google.co.uk/search?hl=en&ie=utf-8&q=resize+partitions+linux](https://www.google.co.uk/search?hl=en&ie=utf-8&q=resize+partitions+linux) You will have to resize filesystems as well

---

### Post by dino99 on 2020-04-19
Erase the packages you does not need from /boot; mainly old kernels

---

### Post by asb3 on 2020-04-19
I booted from a Ubuntu 18.04 livecd and tried to resize the partition using gparted.
It failed.  When I selected the boot partition on /dev/sdb, the current size was the maximum size allowed.
I tried to reduce the size of the /dev/sdb2 and /dev/sdb5 to make room.  Both were "locked".  I unlocked them using by "decativating" them in the pulldown menu.  I was still unable to resize the the other partitions, or to make the boot partition larger. Any suggestions?

---

### Post by Tadaen_Sylvermane on 2020-04-20
My suggestion, drastic as it may seem. Reinstall and don't follow any guides that tell you to split installation into a bunch of partitions, boot especially so small. Just leave it all in /. Maybe put /home or data in it's own partition. Maybe /var as well. But anything these days suggesting such a small /boot is just ridiculous imo unless you have an exact use case. At the very least if I may, reinstall with lvm so you can easily expand partitions as needed. It's great to have even when your OS or whatever is on a single drive for this very purpose.

To explain.

I recently got an older server machine for my home off of craigslist. It came with a 1tb datacenter 7200 rpm drive. As I didn't have an ssd at the time to throw in it I just partitioned it with LVM and away I went. I gave / 250gb as I use LXD containers with LTSP for my desktops / media centers. This gave me plenty of room in /home in the containers. I created a 500gb volume for my mythtv dvr to get it off of my mergerfs pool. I still have 250? ( or less with overhead) available and I can expand those partitions as needed up to that point. It also gives me the ability in the future if I get, say a 500gb ssd to move the / partition to the ssd while the system is live. I haven't tested this yet but I've read about it. Point being LVM gives you a ton of flexibility and is useful for more than just pooling drives / raid devices.

In your case, if you have a drive and you split it up like your existing drive, but you have some free space you can expand a volume. /boot in this case? to give you the room you needed as required.

---

### Post by lvm on 2020-04-20
> **asb3 said:**
> When I selected the boot partition on /dev/sdb, the current size was the maximum size allowed. I tried to reduce the size of the /dev/sdb2 and /dev/sdb5 to make room.  Both were "locked".  I unlocked them using by "decativating" them in the pulldown menu.  I was still unable to resize the the other partitions, or to make the boot partition larger. Any suggestions?

Partition can be grown only if there is some free space adjacent to it, if another partition starts immediately after boot ends it has to be shrunk and moved first to make free space like described in this tutorial: [https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions](https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions)

> **Tadaen_Sylvermane said:**
> My suggestion, drastic as it may seem. Reinstall and don't follow any guides that tell you to split installation into a bunch of partitions, boot especially so small. Just leave it all in /. 

Actually modern ubuntu installer does exactly that - /boot is just a directory. /boot/efi however is a separate filesystem, but there is a reason for it - it has to be FAT32

---

### Post by ProDigit on 2020-04-20
Use Gparted or Disks to change the size.
To install: 
sudo apt install gparted

---

### Post by asb3 on 2020-04-21
I can't increase the size of the /boot partition because the disk is full.
Also mounted on the disk are / and swap.
Here's some pertinent information:
>sudo parted -l
Model: ATA SanDisk SDSSDHP0 (scsi)
Disk /dev/sdb: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   64.0GB  63.8GB  extended
 5      257MB   64.0GB  63.8GB  logical                lvm

u> lsblk        
NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sdb                     8:16   0  59.6G  0 disk  
&#9500;&#9472;sdb1                  8:17   0   243M  0 part  /boot
&#9500;&#9472;sdb2                  8:18   0     1K  0 part  
&#9492;&#9472;sdb5                  8:21   0  59.4G  0 part  
  &#9500;&#9472;ubuntu--vg-root   252:0    0  27.7G  0 lvm   /
  &#9492;&#9472;ubuntu--vg-swap_1 252:3    0  31.7G  0 lvm   [SWAP]

sudo pvdisplay  /dev/sdb5
  --- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               ubuntu-vg
  PV Size               59.39 GiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              15202
  Free PE               0
  Allocated PE          15202
  PV UUID               reAlps-njEI-lQIl-Weoy-r7hW-bbpe-eF96ah

I want to use lvreduce to make the partition smaller so I have room to expand /boot. According to 
[https://www.hiroom2.com/2016/05/19/ubuntu-16-04-extend-and-reduce-lvm-root-filesystem/#sec-3](https://www.hiroom2.com/2016/05/19/ubuntu-16-04-extend-and-reduce-lvm-root-filesystem/#sec-3)
I should use a command like
> sudo lvreduce -r -L -1g /dev/ubuntu-vg-swap_01
Why can't gparted do this? 
As I understand it, the physical partition /dev/stb5 is right next to /dev/stb1 on the drive.
I imagine I have to move /dev/stb5 to make room for the enlarged /dev/stb1. How do I do this?
Can I use gparted to move the reduced /dev/sdb5 to make room for an enlarged /sdb5 without trashing the data?
If not, how do I make a temporary copy the contents of /dev/stb5 so I can copy it back onto the new relocated
partition?  Or is this not required since lvm handles it?

---

### Post by Impavidus on 2020-04-22
You want to resize your /boot partition, but first change the partition to the right of it. That's a slow and error-prone process, so that many people would prefer a fresh install. That partition to the right is in your case an LVM partition, which makes things harder. Gparted doesn't handle LVM, so you need LVM tools. I've got no experience with those.

Next you want to upgrade your system from 16.04 to 18.04. That's another slow and error-prone process, so that many people would prefer a fresh install. If you combine both processes, you only have to do one fresh install to solve both issues, which makes it a clear winner.

---

### Post by ProDigit on 2020-04-23
Odd. Try clearing old kernels from your system by doing:
sudo apt autoremove

Boot should not take up more than 120MB. Mine is 300MB, but <80 megs are used.

---

### Post by asb3 on 2020-04-24
I again attempted to upgrade to 18.04, and I noticed that I had misread  the error message; the partition that was too small was not /boot but /.
The OS is installed on a flash drive that contains /boot, /, and swap space (output from fdisk -l and lsblk included below).
Does  18.04 require more than 59 GiB for /, or is the installer unable to  reclaim data from the swap space?  If the latter, what is a workaround?


>sudo fdisk -l /dev/sdb
Disk /dev/sdb: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000d920a

Device     Boot  Start       End   Sectors  Size Id Type
/dev/sdb1  *      2048    499711    497664  243M 83 Linux
/dev/sdb2       501758 125044735 124542978 59.4G  5 Extended
/dev/sdb5       501760 125044735 124542976 59.4G 8e Linux LVM

>lsblk
sdb                     8:16   0  59.6G  0 disk  
&#9500;&#9472;sdb1                  8:17   0   243M  0 part  /boot
&#9500;&#9472;sdb2                  8:18   0     1K  0 part  
&#9492;&#9472;sdb5                  8:21   0  59.4G  0 part  
  &#9500;&#9472;ubuntu--vg-root   252:0    0  27.7G  0 lvm   /
  &#9492;&#9472;ubuntu--vg-swap_1 252:1    0  31.7G  0 lvm   [SWAP]

---

### Post by CelticWarrior on 2020-04-24
The installer is certainly unable to reclaim space from swap but that's not the issue and your math is completely wrong.
59.6GB is the total capacity of the drive and more than half is swap: 31.7GB (this is totally ridiculous). The root volume is only 27.7GB which indeed may not be enough depending on what you have installed in the system. That's all, really.

+1 for a fresh install.

---

### Post by asb3 on 2020-04-24
Since the installer is unable to reclaim space from swap, can I reallocate some swap space to the / partition?  If so, how?

---

### Post by CelticWarrior on 2020-04-24
Look, I'll be blunt but it's for your own good: If you need to ask DON'T DO IT, don't even try.
Dealing with LVM is way more complex than the usual partitioning. At least one expert commenting here said he himself has no experience with it. Even with conventional partitioning such operations are time consuming and prone to errors. Although there are scenarios where resizing and moving partitions is an option, with caveats but an option, what you intend to do is certainly NOT one of them.

---

