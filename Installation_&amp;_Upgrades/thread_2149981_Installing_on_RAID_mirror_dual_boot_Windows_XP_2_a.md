---
title: "Installing on RAID mirror dual boot Windows XP 2 arrays"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by Aspiegeek on 2013-05-30
I'm trying to figure out how to install Ubuntu 12.04 LTS 64 bit on its own  dedicated RAID 1 mirror, where Windows XP 32 bit is also installed on its own  dedicated RAID 1 array.  

Motherboard is Asus A8V deluxe, with  VIA 8237 and Promise 378 onboard RAID controllers.  XP is up and running fine on  SATA Array 1 on Promise controller, 500 GB.  3 partitions, System, Apps  and Data.

2nd array is 250 GB IDE, also on Promise controller  created as Array 2.  From live USB I was able to create 3 EXT4 primary  partitions on Array 2 with GPARTED, for boot (50gb) , home (175 gb) & swap (7  gb).

Ubuntu  install by default wanted to put the bootloader on  \dev\sdb.    There were about 15 options listed as to where to put the  bootloader, including multiple entries for each of the partitions on  both arrays, and the physical disks as well.  Shouldn't it be either on  either the first (Windows) array \dev\mapper\***, the  second  \dev\mapper\***, or both?  Not sure where to point bootloader.

I went back into the installer to try  to copy the options listed but it crashed to a frozen black screen with  many messages & memory addresses.

Would I be better off using  a software RAID 1 created in Linux instead of the array set up by the  Promise controller?  Caveat--If the Ubuntu array crashes or has a failed member I  still need to be able to load Windows XP.

If the bootloader should go on both arrays, would appreciate step by step instructions for doing that. 

Thanks!
Aspiegeek

---

