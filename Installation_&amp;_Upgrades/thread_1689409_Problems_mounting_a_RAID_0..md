---
title: "Problems mounting a RAID 0."
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by AsherSevyn on 2011-02-16
I just installed a new RAID 0 configuration with 4 1TB hard drives on my new server. My OS is loaded onto a different array. The OS is fine but I am having trouble accessing the Array. I did a df -h and the 4TB isn't showing up.

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/KMHADOOPA01-root
                      141G  855M  133G   1% /
none                  5.9G  232K  5.9G   1% /dev
none                  5.9G     0  5.9G   0% /dev/shm
none                  5.9G   36K  5.9G   1% /var/run
none                  5.9G     0  5.9G   0% /var/lock
none                  5.9G     0  5.9G   0% /lib/init/rw
/dev/sda1             228M   17M  199M   8% /boot

I did a fdisk -l and it shows the drive as sdb1.

How do I get it to be a regular single partition drive?

fdisk -l

Disk /dev/sdb: 4000.0 GB, 3999956729856 bytes
255 heads, 63 sectors/track, 486300 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267350  2147483647+  ee  GPT

---

### Post by srs5694 on 2011-02-16
It appears that you've got a hardware RAID array, so you can treat it like a really big normal disk. The fdisk program will be of limited use, though, since the array is too big to be partitioned using the Master Boot Record (MBR) system used by fdisk. Instead, you must use GParted, GNU Parted, GPT fdisk, or some other tool that can handle the GUID Partition Table (GPT) system.

As with any disk partitioning task, you must partition the disk, create filesystem(s) on the partition(s), and then mount the filesystem(s) in some way. There are multiple ways to do each of these tasks. Check [here](https://help.ubuntu.com/community/HowtoPartition) or [here](http://ubuntuforums.org/showthread.php?t=282018) for an overview of the procedures involved, and post back if you have more specific questions.

---

### Post by AsherSevyn on 2011-02-17
I used a Gparted Live CD to partition and format the 4TB RAID0 Array.

I formatted it with Ext3 and mounted it like this:

sudo mount -t ext3 /dev/sdb1 /mnt

(Was that the correct way to do it?)

I need to verify that my Array is all ready to go for storage purposes.
How do I verify this?

Here is my df -H

Filesystem             Size   Used  Avail Use% Mounted on
/dev/mapper/KMHADOOPA01-root
                       151G   898M   143G   1% /
none                   6.4G   242k   6.4G   1% /dev
none                   6.4G      0   6.4G   0% /dev/shm
none                   6.4G    37k   6.4G   1% /var/run
none                   6.4G      0   6.4G   0% /var/lock
none                   6.4G      0   6.4G   0% /lib/init/rw
/dev/sda1              239M    18M   209M   8% /boot
/dev/sdb1              4.0T   206M   3.8T   1% /mnt

Does that look alright?

Am I good to go?

---

