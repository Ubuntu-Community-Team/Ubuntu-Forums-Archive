---
title: "2 TB limit on partitions"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by kakubei on 2008-08-26
Hello, this is a question I've seen in many places and one problem I have struggled with for a long time until I found the solution and thought I would share it with others in the hopes that it will help someone. 

fdisk has a limit of 2 TB for an individual partition, regardless of the size of your drive (array or not). 

Indeed it is the MSDOS partition table that has this limitation. So if you are having this problem, here is the solution:

1. delete the partition and the table. 
2. create a new partition table. WARNING: creating a new partition table will indeed destroy all the data in your drives. Deleting the partition will NOT destroy data if you create it again with the same beginning. 
3. create a type gtp partition table. 
4. create the new partition with whatever size you want. 

With parted it goes like this

parted /dev/sdx (where sdx is the drive you are trying to resize/partition)

(parted) mktable gpt
(parted) New disk label type?  [msdos]? gpt 
(parted) mkpart primary 0 100%

quit parted
go back in

parted /dev/sdx
(parted) mkfs
Warning: The existing file system will be destroyed and all data on the partition will be lost. Do you want to continue?
Yes/No? yes                                                               
Partition number? 1                                                       
File system?  [ext2]? 

Now you have a partition that doesn't have a 2TB restriction. 

I insist: be careful, recreating a partition table destroys all data. 
Recreating the file system (via mkfs) destroys all data. 

Backup all your data before attempting anything with any partitioning tool!

Cheers.

---

### Post by karlson on 2008-12-17
This recreates a partition table from scratch.  Is there a way to have this type of partition table to be created during installation?

---

### Post by joff13 on 2008-12-17
hi, some more

fdisk has been created in that time were DOS used to lead the scenes. DOS itself has a limit of 2TB in managing partition, because it use 32bit to address sectors: Cylinders/Heads/Sectors triple (given in 10+8+6 bits)

GUID Partition Table (GPT) has been created to get away from this limitation.

GNU created GNU / Parted to work with this new kind of partition tables

Remember that filesystem themselves have some dimension limits..

some links:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://linux.die.net/man/8/fdisk](http://linux.die.net/man/8/fdisk)
[http://linux.die.net/man/8/parted](http://linux.die.net/man/8/parted)

bye

---

### Post by kakubei on 2009-01-05
> **karlson said:**
> This recreates a partition table from scratch.  Is there a way to have this type of partition table to be created during installation?

Not sure I understand the question. You want the install software of Ubuntu to allow you to create this type of partition table while you install the software? 

If that is what you want, I'm pretty sure it cannot be done. Ubuntu installation (as far as I know) does not offer this choice. It only offers you the "usage type" of your partition, that is whether it's /boot or a swap partition, etc.

---

