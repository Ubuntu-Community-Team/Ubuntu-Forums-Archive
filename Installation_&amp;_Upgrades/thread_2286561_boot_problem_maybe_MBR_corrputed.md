---
title: "boot problem maybe MBR corrputed"
date: 2015-07-13
forum: Installation &amp; Upgrades
---

### Post by nv2015 on 2015-07-13
i am trying to repair a ubuntu install . on booting it errors out


error: no such disk 
error: no such device

i installed boot-repair and got this output 
[http://paste.ubuntu.com/11871118](http://paste.ubuntu.com/11871118)

please help.

---

### Post by nv2015 on 2015-07-13
sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   312,498,175   311,996,418  ee GPT

---

### Post by Bucky Ball on 2015-07-13
Welcome. What did you have to start with, what was wrong with it that you tried to repair, and how did you go about repairing it, please. :)

Looks like install got somehow mixed up. Was the last install in EFI and you have attempted to repair Ubuntu with EFI off in the BIOS? Did you have secureboot on or off?

You have this:

```
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.
```

... and this:

```
Error: no partitions
```

I'm unsure what's going on there, but hopefully someone can help. Let us know the answers to the questions at the beginning of my post, might shed a bit more light. :-k

---

### Post by oldfred on 2015-07-13
Normally if using gpt, your fdisk shows just one gpt partition in the gpt protective MBR. That is to show drive is used for gpt for old tools that only know MBR(msdos) like older versions of fdisk.

But if drive really is gpt, run this:
sudo parted -l
or 
       sudo gdisk -l /dev/sda

---

### Post by nv2015 on 2015-07-15
so this machine lost power and seems the fiels system crashed. when i boot up it errors out and cant find the device. 
today i used a usb drive to boot and run fsck and heres what i got


ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

---

### Post by nv2015 on 2015-07-15
here's output of parted

ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label                                  

Model:   (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  16.0GB  16.0GB  primary  fat32        boot, lba
 2      16.0GB  16.0GB  32.3kB  primary

---

### Post by nv2015 on 2015-07-15
heres out put of gdisk

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 312500000 sectors, 149.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): DD6C61FA-45A4-4538-8171-FF87967353BA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312499966
Partitions will be aligned on 2048-sector boundaries
Total free space is 312002269 sectors (148.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          499711   243.0 MiB   8300  Linux filesystem
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by nv2015 on 2015-07-15
really appreciate everyones help. this machine has been used for code repo over 2 years and has lots of data on it
thanks

---

### Post by oldfred on 2015-07-15
You need to know if drive really is MBR(msdos) or gpt(GUID). 

Your gdisk output is showing both or corruption on that which needs to be resolved first.
You can use fixparts to convert to MBR or use gdisk and the w command to convert to gpt. But if not in original partition structure, you cannot recover data.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Not sure which of these?

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Then you need to list backup superblocks and see if fsck will work.

       
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5

---

