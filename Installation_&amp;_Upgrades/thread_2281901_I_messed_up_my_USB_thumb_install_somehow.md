---
title: "I messed up my USB thumb install somehow"
date: 2015-06-10
forum: Installation &amp; Upgrades
---

### Post by virgodave61 on 2015-06-10
When I run Ubuntu off my USB thumbdrive, I keep getting error messages saying that I'm out of memory space.
Then if I check it with gparted I have one partition labeled sdb1, Fat32, 5GB used and 14.44 free, with boot/lba
under flags, does anyone know what I did wrong or how to fix it.
Thanks in advance,
Dave

---

### Post by yancek on 2015-06-10
Can you post the specific error/warning message?  Memory is not the same as hard drive space or space available on your flash drive.

---

### Post by virgodave61 on 2015-06-10
It says " This computer has only 88.1 MB disk space remaining", like I said I'm running off a USB thumb drive.
Computer properties say 3.7 GB used and 186.3 MB free, the thumb drive is a 14 GB partition.
The hard drive, which isn't in use because its running on the thumb drive says 16GB used and 132 GB free.
Thanks,
Dave

---

### Post by ubfan1 on 2015-06-10
Sounds like you might have use "persistent" on the creation of the 16G live media.  Now the FAT filesystem is limited to a maximum file size of 4G, so the writeable part of your install is a 4G file named casper-rw.  You can get around this limit by making an ext2 partition (or ext4 with journaling turned off) bigger than 4G with the label "casper-rw".  Also, although I have not done this, is to make another file called home-rw or something like that for another 4G of storage for your home directory.  There are several threads here or questions in askubuntu on setting this up, it's not hard.

---

### Post by C.S.Cameron on 2015-06-10
+1

casper -rw is similar to a / partition on a full install,
home-rw is similar to having a /home partition on a full install.
Either can exist as files or partitions on a persistent install.
The files are limited to 4GB, (being FAT32), the partitions, (being ext4, 3 or 2), are unlimited.
It sounds like you may have tried doing a software update, 
this is a no-no with persistent drives as it quickly fills the persistence files/partitions.
You can mount the casper-rw and home-rw files to delete stuff, booting fron a second install of linux.

---

### Post by virgodave61 on 2015-06-11
Wow guys thanks that will get get me going, I'm sure. If I have to I will start over at least I know what not to do.
Thanks!
Dave

---

