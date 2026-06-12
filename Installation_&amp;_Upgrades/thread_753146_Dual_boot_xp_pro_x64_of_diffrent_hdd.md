---
title: "Dual boot xp pro x64 of diffrent hdd"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by dark68 on 2008-04-12
At the moment im trying to install my windows XP pro x64 too boot off grub my setup is layed out like this so far

2 hdd: 
one sata (xp is on this) and this is the master drive
one IDE (ubuntu is on this) and this is the slave drive but is currently set to boot first in the bios hence why i want to add xp to the grub menu to boot.

ive read in other threads that i need to add a few lines to the 'menu.lst' but so far this has been unsuccessful here is what i currently have in my menu.lst to try and boot xp,

> title		Winwods XP Pro x64
root (hd0,2)
savedefault
makeactive
map(hd0)(hd1)
map(hd1)(hd0)
chainloader+1

this dose show a menu item but when i select it to boot xp it says no partition found (ubuntu can view my ntfs drive so i know its there and working)

this is what my fdisk -l looks like;
> 
Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74317431

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11b011b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48640   390700768+   7  HPFS/NTFS


and my device map look like:
> (hd0)	/dev/hda
(hd1)	/dev/sda

Any help would be great i have look at the other threads and tried but i must be missing something.

---

### Post by Pumalite on 2008-04-12
Your problem is the mix of IDE and SATA drives.
Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)
[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

I'd install both OS's in one drive (SATA?) and have the IDE as storage or separate /home for Ubuntu.

---

### Post by dark68 on 2008-04-12
I would its just alot of hassle and time updating, 

I was hoping a couple of lines in the menu.lst would fix the problem 

If i did reinstall would i be better off using the x64 version of ubuntu as im waiting for 4 gb of ram to arrive that why i put 64x xp on my box dose ubuntu have the same memory addressing problems as windows or would it be ok with the 32 bit version??

---

### Post by Pumalite on 2008-04-12
I'd go 64 bit.

---

### Post by dark68 on 2008-04-12
ta for the help decided to reinstall xp and ubuntu on the same hdd and use the other hdd for data storage,

I do think that ubuntu should include in the next version support in the install for including os on other hdd on grub because i know if they were on the same hdd i wouldnt of had this problem.

It would help the less linux savy user. Like me.

---

### Post by Pumalite on 2008-04-12
If you had 2 SATAS or 2 IDE, there would be no problem.

---

