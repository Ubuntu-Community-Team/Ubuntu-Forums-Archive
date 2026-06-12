---
title: "60GB laptop HDD partitioning strategy before install Lubuntu"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by gigi3 on 2014-07-24
Hi all, I have an Acer Travelmate 2420 old laptop with a dual boot 60GB HDD (Windows XP and Ubuntu 14.04). It works fine, apart from the well known shutdown problem (the laptop doesn't power off) but this is another story. Now, I have a second HDD to play with ... it's identical to the first one because it comes from another even older Acer laptop (Aspire 1360, with broken DVD drive and only 512MB of RAM) that I don't want to keep any more. This second HDD has the same Windows XP structure with C and D FAT32 partitions as the first one but for this drive I'd like to use it entirely with Linux. I want to install Lubuntu, in order to my old Travelmate hardware (Intel Celeron M 1.50GHz, graphics Intel 915GM, 1GB RAM but this will be doubled) as 'faster' as possible. For this second HDD I'm looking for advice for a good partition layout. The laptop need to have a simple 'home setup' so I'm thinking about three partitions only, swap (2GB), root and a data partition, as suggested by coffeecat. I'm not sure about the sizing of these partitions (and the partition type to assign to the data partition, assuming root as ext4) and if it's better to consider further partitions.
Gigi

---

### Post by sudodus on 2014-07-24
If you want to hibernate you need swap size at least the same size as RAM in Gibibytes, so 2 Gibibytes. If you make it 2560 MB, there will be some margin. Otherwise I think 512 MB swap will be enough.

With a data partition your root partition can be rather small, but do not make it too small, I suggest 20 GB, and the rest of the drive space can be used as a data partition. You could even use less, even as low as 12 GB, depending on how many program packages you want to install, and how much personal data files will be in the home partition. If you are good at moving data from 'home' to 'data', you need less disk space for the root partition. But it must be enough to create temporary files (which might be big) and to avoid disk fragmentation.

/dev/sda1 - root partition - 20 GB - ext4 file system 
/dev/sda2 - extended partition - all remaining unallocated drive space (no file system)
/dev/sda5 - swap partiton - 512 MB (logical partition inside the extended partition) - linux-swap (no file system)
/dev/sda6 - data partition - all remaining unallocated drive space inside the extended partition) - NTFS file system if used also from Windows

-o-

I have my root partition on a 60 GB SSD and use a data partition (no separate home partition). I use most of the SSD for the root partition. My data partition is located in a HDD and it is auto-mounted via /etc/fstab.

---

### Post by gigi3 on 2014-07-24
Thanks sudodus for your advice. I will have only Lubuntu installed on this HDD, no Windows at all, so I was wondering if it is better an ext4 file system for the sda6 data partition rather then NTFS. In fact I don't know the pros and cons about these file systems type under Linux.

---

### Post by yancek on 2014-07-24
If you are not going to have a windows system on the computer and are not going to be accessing your data partition from another networked local computer, use ext4 or ext3 or any Linux filesystem.  ext4 is the most used and the default on most newer Linux systems.

---

### Post by sudodus on 2014-07-24
> **gigi3 said:**
> Thanks sudodus for your advice. I will have only Lubuntu installed on this HDD, no Windows at all, so I was wondering if it is better an ext4 file system for the sda6 data partition rather then NTFS. In fact I don't know the pros and cons about these file systems type under Linux.

> **yancek said:**
> If you are not going to have a windows system on the computer and are not going to be accessing your data partition from another networked local computer, use ext4 or ext3 or any Linux filesystem.  ext4 is the most used and the default on most newer Linux systems.

+1

If you are not going to have a windows system on the computer, it will be better to have an ext4 file system in the data partition. It will be faster and at least as reliable, and the linux file permissions will be managed in a correct way.

---

