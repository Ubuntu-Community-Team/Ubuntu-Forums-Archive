---
title: "best way to partition"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by rkakkar on 2006-11-30
i have a 80 GB hard disk. what would be the best way to parition it? My requirements are:

1) Windows XP (to run ITunes and other windows specific software)
2) Ubuntu
3) Data Drive (FAT32 so that I can access it in windows for my mp3 files in itunes)

I want the least number of partitions as possible. What do you'll recommend?

I have 512MB ram currently.

---

### Post by pay on 2006-11-30
Install Windows with an NTFS partition (I have had problems with fat32 and windows system files)and make a fat32 partition but leave unpartitioned space. Install Ubuntu with the option install in unused space.

---

### Post by rkakkar on 2006-11-30
> **pay said:**
> Install Windows with an NTFS partition (I have had problems with fat32 and windows system files)and make a fat32 partition but leave unpartitioned space. Install Ubuntu with the option install in unused space.

thanks! but i heard that creating fat32 partitions greater than 32 gb cause a problem?

---

### Post by alican timur on 2006-11-30
Well, because linux can see NTFS but windows can't see reiserfs, you can divide it just into two partitions, but you have to keep your music in the windows partition (for itunes). So, I'd say like, 60 NTFS, and the rest for reiserfs and swap.

---

### Post by rkakkar on 2006-11-30
> **alican timur said:**
> Well, because linux can see NTFS but windows can't see reiserfs, you can divide it just into two partitions, but you have to keep your music in the windows partition (for itunes). So, I'd say like, 60 NTFS, and the rest for reiserfs and swap.

will i be able to write on the ntfs partition in ubuntu?

---

### Post by pay on 2006-11-30
Not out of the box but with some exoerimental drivers you can. Look at this [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

