---
title: "upgrading to 11.04 but out of space"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by chris_linux on 2011-11-23
I created a new partition that is 40 gigs and have it auto mounted under my home directory. When I try to upgrade to 11.04 of ubuntu it says I don't have enough space in /. Is there a way to get / to use some of the space in the partition I created. The partition is in /home/chris/disk3.

Thanks,
Chris

---

### Post by BC59 on 2011-11-23
Please open a terminal CTRL+ALT+T type and post the result


```
sudo fdisk -l
```

---

### Post by BC59 on 2011-11-23
And this as well:

```
sudo parted /dev/sda print
```

---

### Post by chris_linux on 2011-11-23
Below is the output from those two commands.

chris@chris-Vostro-1500:~$ sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbedffd6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       38876       43336    35832982+  83  Linux
/dev/sda2           43337       45248    15358140   82  Linux swap / Solaris
/dev/sda3           50604       53152    20474842+   7  HPFS/NTFS
/dev/sda4           45249       50603    43014037+   c  W95 FAT32 (LBA)

Partition table entries are not in disk order
chris@chris-Vostro-1500:~$ sudo parted /dev/sda print
Model: ATA WDC WD5000BEVT-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size    Type     File system     Flags
 1      320GB  356GB  36.7GB  primary  ext4            boot
 2      356GB  372GB  15.7GB  primary  linux-swap(v1)
 4      372GB  416GB  44.0GB  primary  fat32           lba
 3      416GB  437GB  21.0GB  primary  ntfs

chris@chris-Vostro-1500:~$ 

sda4 is the newest partition I created that has the free space. BTW: I'm using a bootmanager from terabyte that separates my Windows partition from linux.

Thanks for your help,
Chris

---

### Post by chris_linux on 2011-11-23
I had some free space near the linux partition so I increased the size of SDA1 to 70+ gigs. Now I need to run resize2fs but it doesn't look like it'll let me since its the boot partition. Is there a way to resize it or do I need to use a live boot cd to do it. Or would resize_reiserfs do it without the live cd.

Thanks,
Chris

---

### Post by BC59 on 2011-11-23
> **chris_linux said:**
> I had some free space near the linux partition so I increased the size of SDA1 to 70+ gigs. Now I need to run resize2fs but it doesn't look like it'll let me since its the boot partition. Is there a way to resize it or do I need to use a live boot cd to do it. Or would resize_reiserfs do it without the live cd.

Thanks,
Chris

The only way to do changes to partitions is when they are unmounted. So you have to boot from Live CD and use Gparted.

When you work with partitions **first do a backup.**

To use a Linux system you need basically 2 partitions
the **/** and one **swap**.
I don't see a **/** on your partitions and the swap I see is huge.

The rule of thumb says the swap has to be something like the double of your RAM. Means if you have 6G RAM you need about 12G of swap.

Now the most common partition for a Linux installation should be like:
7-8G for the **/ **(the system)
8-12G for **swap** (depends on your RAM)
and the rest for **/home**

You don't need to assign a special partition for /boot, /tmp etc because there are for special purposes. 

Now, to resize a partition there are two ways, one going towards  left and the other going towards right. Going towards right is always much easier. 

To understand this put your partitions to a line so we have

sda1  sda2  sda3  sda4.

To expand a partition you need free "unallocated" space.
So sda1 can only be expanded to the right and needs free space from sda2. Means you can delete swap (it's empty) and expand sda1 to the right. Then you can assign the rest of the unallocated space as sda2 swap.

---

