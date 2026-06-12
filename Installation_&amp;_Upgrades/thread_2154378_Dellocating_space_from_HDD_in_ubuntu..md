---
title: "Dellocating space from HDD in ubuntu."
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by baskivs on 2013-06-14
Hi All,

I am new to ubuntu... i have a below query..

In  my laptop i have installed Ubuntu 12.04 and it is partation as sda1 & sda2 .. 
sda 1 size is 300GB  (VFAT)
sda2 size is 850 GB (EXT4)


now i would like to deallocate 500GB space from sda2 to install Windows. without uninstalling ubuntu.


kindly help me on this.. 

Thanks in advance..

Baski

---

### Post by ajgreeny on 2013-06-14
Which version of windows and which Ubuntu?  Why not install Windows on to sda1 which is your vfat (fat32) partition, as the windows installer will see that but will not see your ext4 partition.  Perhaps that is that already full of data?

If you want to install to sda2 you will have to run a partition editor such as **gparted** on the live ubuntu system and shrink the installed Ubuntu partition sda2 by grabbing the right hand end and pulling it to the left until you get the partition sizes you want.  You should then leave the unallocated space as that; do not attempt to format it just leave it alone as unallocated.

However, do not jump into this immediately as I think that I have seen that there can be problems installing Windows at the far end of a disk of that size.  I may be wrong, so wait for more answers.  After installing Windows you will certainly have to reinstall grub in order to get your ubuntu to boot as windows will take over the boot loader and not see your linux installation.

---

### Post by sanderj on 2013-06-14
+1 to "Dellocating" in your post title ... I assumed it had to do with Dell ... ;-)

---

### Post by Mark Phelps on 2013-06-14
I would not attempt to install Win7 to the FAT32 volume, as it requires an NTFS volume for installation. Plus, it's best to let the Window installer format its own partition as part of the installation.

---

### Post by ajgreeny on 2013-06-14
> **Mark Phelps said:**
> I would not attempt to install Win7 to the FAT32 volume, as it requires an NTFS volume for installation. Plus, it's best to let the Window installer format its own partition as part of the installation.

I did not mean to install to the fat32 partition, just to use it instead of messing with a Ubuntu OS that presumably is working well.  I doubt you can even install Windows without formatting during the install, but it's so long since I did it that I can't remember anything about it.

Is there any truth in my idea about windows not working properly if at the back-end of a large disk, or did I dream that up?

---

