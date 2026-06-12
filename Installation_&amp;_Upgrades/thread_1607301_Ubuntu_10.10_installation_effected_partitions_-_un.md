---
title: "Ubuntu 10.10 installation effected partitions - unable to boot."
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by AndreLeComte on 2010-10-27
When running GParted Partition Editor from the Ubunutu CD, the first hard drive sda (Windows Vista) has the warning 'Can't have a partition outside the disk!' and the second hard drive sdb (Ubuntu 10.10) has the warning 'unrecognized disk label'.
How can this be repaired without losing the data on sda?

---

### Post by viralmeme on 2010-10-27
> **AndreLeComte said:**
>  'Can't have a partition outside the disk!'

[http://ubuntuforums.org/archive/index.php/t-352723.html](http://ubuntuforums.org/archive/index.php/t-352723.html)

[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)

---

### Post by AndreLeComte on 2010-10-27
Thanks for the references. The discussions about manually adjusting the partitions are complicated. Would it be better to restore Windows on hard disk sda using the Vista CD then format hard disk sdb and install Ubuntu 10.10 on sdb again?

---

### Post by AndreLeComte on 2010-10-27
The Windows Vista CD only detects one hard disk and that hard disk is all unallocated space. Will the Rescatux CD or Super Grub2 Disk be able to fix the partitions?

---

### Post by AndreLeComte on 2010-10-27
Windows Vista is detected by Super Grub2 Disk and needs to be repaired. The Windows Vista CD cannot start the repair because it can not detect Windows Vista. Any ideas?

---

### Post by Stephen Holliday on 2010-11-13
I have had the same problem in the past which I have overcome simply by re-installing Ubuntu and GRUB recognises the windows partition and gives to 
option of booting to it.

Your suggestion of reinstalling Windows and then adding ubuntu again would word but I have always found that a bit of a pain since I have a lot of programs on windows. (Not sure why I bother though because I only use windows for a few tasks so don't really need all the programs I have installed)

:guitar:

---

### Post by AndreLeComte on 2010-12-16
I downloaded Active@ Boot Disk from [www.ntfs.com](www.ntfs.com) and I can see that my files still exist. I will try install an operating system on the empty drive and recover the files manually.

---

