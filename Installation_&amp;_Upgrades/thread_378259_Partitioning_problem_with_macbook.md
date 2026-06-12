---
title: "Partitioning problem with macbook"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by lkogler on 2007-03-07
Hi there, I'm a longtime linux user, but this is my first time trying ubuntu.  I am trying to install it on a new MacBook, and have read several good guides online.  My problem is this: after using the Mac Boot Camp software to make a "windows" partition on my hard drive and booting into the kubuntu installation CD, I can't seem to get the partitions created properly using the installer software (QTParted, i think).  Looked around online, but I can't seem to find any solution.

From the installer, I select "manually edit partition table," since I don't want to delete the OSX partition that is already there.  Then the installer comes up with a list of 6 partitions, which are all listed as "primary," according to the "property" button.  (How can I have 6 primary partitions?  This is a mystery to me...).  This is what the partition table looks like:

Number | Partition | Type | Status | Size
01  | /dev/sda-1  | free | | 0.00 MB
02  | /dev/sda1   | fat32 | Active/Hidden | 200 MB
03  | /dev/sda2   | hfs+ | Active/Hidden | 34 GB
04  | /dev/sda-1  | free  | Hidden | 128 MB
05  | /dev/sda3   | unknow | Active/Hidden | 40.21 GB
06  | /dev/sda-1  | free | Hidden | 0.01 Mb

I try deleting partition 5, which actually deletes partitions 4-6 and replaces them with one line: 
04  | /dev/sda-1  | free  |       | 40.34 GB

Now, I would like to create a / partition and a swap partition.  I try selecting the newly created free space and clicking "create".  If I allocate less than the total free space for a new partition, then the remaining free space appears in the table, but the "Create" button is not active when I select that space.  I suppose this is because I actually need to create an extended partition since I already have 4 partitions listed.  So I undo the creation of the primary partition, and instead try  to create an extended partition in the free space.  However, after I click "OK", it does not appear to have actually created any partition.  The space is still listed as free, and I cannot find an option to create logical partitions anywhere.  

It has been a long time since I used fdisk, but I thought maybe I should give that a try.  But though the device is listed as "/dev/sda" in the installer, the command "fdisk -lu /dev/sda" returns "Cannot open /dev/sda".   Maybe I am just being stupid?

Any insight would be greatly appreciated.

Thanks,
Laura

---

### Post by Kateikyoushi on 2007-03-07
The 3 partitions were deleted because actually that was only one partition with free space before and after.

Try fdisk -l without /dev.

---

### Post by ouilsen on 2007-03-07
What definitely works is, delete /dev/sda3 with *Parted and let (K)Ubuntu partition the free space automatically by the installer. It will create a root and a swap partition.

---

### Post by lkogler on 2007-03-08
Ok, I still couldn't get fdisk or the manual partition editing to work, but I did as you suggested and let the installer automatically partition the free space.  This seems to have worked, so thanks!

---

