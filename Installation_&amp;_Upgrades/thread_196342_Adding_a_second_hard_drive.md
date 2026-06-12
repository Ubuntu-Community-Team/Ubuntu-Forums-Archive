---
title: "Adding a second hard drive"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by vishnu on 2006-06-14
I have a hard drive that I took from my Windows PC.  In Windows I deleted the partition.  I try running the following command and get the following message:

sudo fdisk /dev/hdd

PRODUCES THIS MESSAGE:
[I]Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.

The number of cylinders for this disk is set to 77545.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): [/I]

I then type "w" and everything looks good.  If I type the fdisk command again I get this:
[I]The number of cylinders for this disk is set to 77545.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)[/I]

I then format using this command: sudo mkfs -t ext3 /dev/hdd

The drive appears as hdd in System - Disks.  I cannot get it to appear as a drive in Nautilus and I tried mounting it but find I can't copy and paste to the /media/drive2 folder.

Any ideas?

---

### Post by iball on 2006-06-14
Can you mount it using the command line?  If so, what is the command that you used to do so.

I assume that you have created /media/drive2 as a mount point.  You could give it a more descriptive name, such as /media/mp3, but that doesn't matter.  You should add the following line to /etc/fstab:
```
/dev/hdd       /media/drive2     ext3    defaults        0       2
```
This should mount it when your system boots, and allow users read and write access.

Also, when you have mounted the drive, check the permissions for /media/drive2.  You should make sure that your user has write permissions to write data to the drive, and read and execute to access the contents.

I hope this helps
--Ian

---

