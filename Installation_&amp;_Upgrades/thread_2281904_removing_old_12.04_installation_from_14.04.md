---
title: "removing old 12.04 installation from 14.04"
date: 2015-06-10
forum: Installation &amp; Upgrades
---

### Post by sequimbob on 2015-06-10
I am currently running Ubuntu 14.04.  I upgraded from 12.04.  My grub show an entry for opening 12.04. When I click on the grub entry, it opens 12.04. I don't need 12.04 any longer an I would like to remove 12.04 to free up disk space.  How do I do this? I have looked in the software center and no entry for 12.04 exists.  I also looked in Synaptics package  manager.  It comes up with a 12.04 entry but when I try to update it, it want to install 12.04. Can I use apt-get autoremove for this action?
I am running a HP Pavilion g7-2069wm Notebook PC 64bit14 with 6 gb of ram. Can anyone help me on this matter?

---

### Post by v3.xx on 2015-06-10
You upgraded to 14o4, but still can boot 12o4.  I don't think you upgraded.  What did you do?

---

### Post by sequimbob on 2015-06-10
My grub has both 14.04 and 12.04.  When I upgraded, I just followed the directions.  14.04 is up and running, but if I go back and select 12.04 it boots up.  There are definitely two different distros on my machine.

---

### Post by v3.xx on 2015-06-10
Please verify the version of both.
```
lsb_release -a
```
Whats your partition layout look like?
```
sudo fdisk -l
```
How did you upgrade?  What command or gui was used?  I am trying to understand why a version upgrade looks like a fresh install.

---

### Post by sequimbob on 2015-06-11
here are the outputs of each of the above

bob@HP-g7:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty
bob@HP-g7:~$ 

bob@HP-g7:~$ sudo fdisk -l
[sudo] password for bob: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e5e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1952151551   976074752    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    98590904    49295421    c  W95 FAT32 (LBA)
/dev/sdc2        98592766   156301311    28854273    5  Extended
/dev/sdc5       144818176   156301311     5741568   82  Linux swap / Solaris
/dev/sdc6        98592768   144818175    23112704   83  Linux

Partition table entries are not in disk order
bob@HP-g7:~$

---

### Post by v3.xx on 2015-06-11
You have one linux install on sdc/6.  The other on sda?  Its looking like two installs.
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
Ok, use:
```
sudo parted -l
```
Are you running encryption?

---

### Post by sequimbob on 2015-06-13
No, no encryption.  It appears that the Ubuntu 12.04 is on a external HDD. I thought that when installating 14.04 that the old 12.04 would have been over written.  Can I just erase the partition that 12.04 is on and then edit grub to get rid of 12.04?

---

### Post by v3.xx on 2015-06-13
> Can I just erase the partition that 12.04 is on and then edit grub to get rid of 12.04?
Not exactly.  Removing 12o4 will leave you with a unbootable system.  It will ne necessary to reinstall grub.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reinstall+grub&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reinstall+grub&sa=Search&cof=FORID:9)

You could go ahead and install to the location you wanted to in the first place and have a second install for backup.  Thats something I do as part of my backup plan.  If you do this, remove 12o4 first and leave it as free space, that way there is no chance of mistake.

---

### Post by sequimbob on 2015-06-14
Ubuntu 14.04 is installed on sda, which is where I want it.  Ubuntu 12.04 is on sdc6.  As I understand you, I can remove 12.04 from sdc6 and install a back up copy of 14.04 on sde6.  Is this correct?  If so, do I do this with "sudo apt-get remove ubuntu 12.04 ubuntu 14.04+".  How do I insure that it doesn't overwrite my current install of 14.04?. 

below is the output of sudo parted -l
since I inserted/removed some flash drives,  12.04 is now on sde6 (which is a portable usb 80gb hard drive)

bob@HP-g7:~$ sudo parted -l
[sudo] password for bob: 
Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot
 2      538MB   744GB  744GB   ext4
 3      744GB   750GB  5873MB  linux-swap(v1)


Model: HP External HDD (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: WDC WD80 0UE-00HCT0 (scsi)
Disk /dev/sde: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  50.5GB  50.5GB  primary   fat32           lba
 2      50.5GB  80.0GB  29.5GB  extended
 6      50.5GB  74.1GB  23.7GB  logical   ext4
 5      74.1GB  80.0GB  5879MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.
Ignore/Cancel? i                                                          
Model: Unknown (unknown)
Disk /dev/sr1: 175MB
Sector size (logical/physical): 512B/2048B
Partition Table: mac

Number  Start  End    Size   File system  Name                        Flags
 1      512B   1535B  1024B               CDEveryWhere 2.0 Part. Map
 2      1536B  904kB  903kB  hfs          CDEveryWhere Hybrid Volume


bob@HP-g7:~$

---

### Post by v3.xx on 2015-06-15
Apt-get commands are no good for this.

You seem to lack enough partitioning experience to feel comfortable at this.  Maybe it would be  better to look at other options.

You could upgrade the 12o4 install to 14o4 and not have to do any partitioning.
```
update-manager -d
```
With any luck that will generate a popup asking if you want to upgrade to 14o4.

---

### Post by sequimbob on 2015-06-15
Okay, that sounds like a good idea.  Thanks.

---

### Post by sequimbob on 2015-06-16
Thanks v3.xx for all your help.  Greatly appreciated

---

### Post by v3.xx on 2015-06-16
Happy (RV) trails :)

---

