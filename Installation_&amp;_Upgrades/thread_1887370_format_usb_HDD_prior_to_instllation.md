---
title: "format usb HDD prior to instllation?"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2011-11-26
do i need to format USB hard disk drive before installing ubuntu?

---

### Post by Enigmapond on 2011-11-26
No...it should format itself when you install. If you are doing a stick for a virtual box it will format to FAT or FAT32...if just straight install on USB it will format to ext*.

---

### Post by Matrix01 on 2011-11-26
and,
are everythings in USB HDD get wiped?
i have to back up.

> **Enigmapond said:**
> No...it should format itself when you install. If you are doing a stick for a virtual box it will format to FAT or FAT32...if just straight install on USB it will format to ext*.

---

### Post by darkod on 2011-11-27
Depending what are you actually planning to do. You don't have to allocate all the ext HDD for ubuntu. You can keep for example one or two ntfs partitions on it, and then after them leave unallocated space (not belonging to any partition). During the install tell ubuntu to install there either by manual partitioning or one of the auto methods.
Just be careful NOT to use 'erase and use whole disk' because that will ERASE the whole ext HDD.
Also make sure you install grub bootloader to the ext HDD not to interfere with your booting when it's not plugged in.

---

### Post by coldraven on 2011-11-27
I have a 1TB USB HDD, it came formatted with FAT32.
It worked straight away and I copied some files without any problem.
But if you want to copy files greater than 4GB (most movies) you need to change the format.
I chose NTFS because Windows, Mac and LInux can all use it.
Just run gparted, be careful to select the correct drive in the drop down menu on the top right corner of the window.
It will of course delete all data on the drive so backup your stuff first.

Ooops! I mis-read your post, ignore me :) 
I must be hung-over from last night in the pub!

---

### Post by Matrix01 on 2011-11-27
my usb hdd has 1 TB as wel.

> **coldraven said:**
> I have a 1TB USB HDD, it came formatted with FAT32.
It worked straight away and I copied some files without any problem.
But if you want to copy files greater than 4GB (most movies) you need to change the format.
I chose NTFS because Windows, Mac and LInux can all use it.
Just run gparted, be careful to select the correct drive in the drop down menu on the top right corner of the window.
It will of course delete all data on the drive so backup your stuff first.

Ooops! I mis-read your post, ignore me :) 
I must be hung-over from last night in the pub!

---

