---
title: "Dual Boot with multiple HDs"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by blakep2 on 2014-08-26
Currently I have a system with a 120GB SSD and a 1TB HDD.  Windows is installed on the SSD currently and the HDD is NTFS formatted.  I would like to dual-boot ubuntu with windows but I do not know what the best way to configure this setup.   I could easily give ubuntu 70GB of the solid state drive but I am afraid I will run out of space in this partition.

I guess what I am asking(which may be completely impossible) is there any way to configure the 2 drives so that Ubuntu sees something like 70GB SSD and 500GB HDD as one single directory tree?  Maybe placing the most frequently used files on the SSD?  I have done some research and it seems using LVM to RAID the drives may be the right solution, but I am not sure.  Has someone done this before?

Any other suggestions for this setup would be appreciated as well.

---

### Post by fantab on 2014-08-26
Is that Windows 7 or 8? Was this preinstalled?

Boot with Ubuntu DVD/USB... Try Ubuntu
Post the output of the following:
```
sudo parted -l
```

Generally we'd advice to keep both Windows and Ubuntu separate disks. However, Since you have a SSD (which loads faster than Hdd) it won't be bad idea to at least keep Ubuntu '/' root partition (where Ubuntu keeps its system files) on the SSD.

In my view, about 25Gb for Ubuntu's '/' is plenty. So make space on SSD for about 25gb and Install Ubuntu '/' on it. For you data you make your 500gb HDD partition and make it '/home' partition to store your data.

---

### Post by blakep2 on 2014-08-26
It is Windows 7.  I installed it myself.  I built the machine myself there is currently nothing on Windows.  The plan was to dual-boot and in my experience it tends to be easier to install Windows first then Ubuntu.

Here is the output:

Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   120GB  120GB  primary  ntfs




Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs




Warning: /dev/sdc contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?

---

### Post by yancek on 2014-08-26
Not knowing what your primary use of the computer will be it is difficult to give specifics but creating a partition on the SSD for the Ubuntu installation and then either a separate /home partition on your other drive or a separate data partition would work.  You would need to resize/shrink the windows partition on the SSD to do this and it is best to do from windows.  You would also obviously need to shrink the 1TB drive as it now contains just one huge partition.  During the install, select to install the Ubuntu filesystem to the SSD and create a separate home partition.  All will need to be formatted and that option is available in the installer.  The link below gives some good info on partitioning in Linux and has a number of links for additional information as well as how to install 14.04.

 [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by fantab on 2014-08-27
To install ubuntu '/' on SSD /dev/sda:
Boot Windows. And [Shrink]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html") your windows to 100-90Gb, which leave 20-30Gb to install Ubuntu to.
You must also create partitions on your second drive:
Swap Partition about 2-4Gb
/home partition for Ubuntu

NTFS partition can be used in Ubuntu to read and write but windows can't to ext4.
So you can share your certain data between Win and linux.
If I were you:
500gb NTFS
500gb ext4 /home
plus Swap.

Reboot Windows a couple of times... if Windows needs to run 'filesystem' check it will.

Boot Ubuntu DVD/USB; using Gparted setup the 20-30Gb 'unallocated space' to ubuntu:
Make a new Primary Partition and format is with ext4.

Install Ubuntu: choose 'Something Else' and setup the parition:
use as=ex4
mountpoint= /
format

Good Luck...

---

