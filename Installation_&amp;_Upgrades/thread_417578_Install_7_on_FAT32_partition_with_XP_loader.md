---
title: "Install 7 on FAT32 partition with XP loader"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by new_user10 on 2007-04-21
I have been told to try Ubuntu 7 -- the only way I can use it is if I can boot from a FAT32 partition -- this will not be the primary partition -- that already has a dual boot with windows XP and another OS.

So I would need to put Ububtu 7 into a LOGICAL DRIVE on the EXTENDED partiion of a FAT32 partitioned disk, sorry, that is the only way I can do it.

Ubuntu would also have to be loaded from the XP boot loader, which currently holds the existing dual boot (it would make a tri-boot).

(I might add, that one of the biggest problems with linux acceptance into the mainstream is exactly this above problem.  I contribute to major support sites on the net where a LOT of people lose their XP installs from trying to make a linux install peacefully coexist with the existing XP installation, without trashing it.  If ANY linux-type installation could solve this problem, they would win over the mass of the XP community, believe me !!)

So, after that aside, please be specific as to the installability of Ubuntu on an extended FAT32 partition, using the existing windows XP boot loader.

Thank you.

---

### Post by louieb on 2007-04-21
To install any Linux distro you need a partition formated with a Linux file system. (ext3 and risnerfs are the common ones) Doesn't matter if the partition is primary or logical. The XP Boot manager can be configured to boot Linux. You have to do it, no automation here.
Given your criteria of using[LIST]
[*]use windows boot loader - yes.
[*]install on extended partition - yes
[*]install on a fat32 formated partition -no[/LIST]So there you go Linux does not install on a fat32 formatted partition. One reason is fat32 does not support file ownership or read, write and execute permissions. Security is built into the core of Linux.
BTW heres some good reading on the subject of Linux [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")
:guitar:

---

### Post by new_user10 on 2007-04-21
Thanks for the individual point-by-point answers, that helps a lot.

So if the partition was (1) NTFS or better still (2) space left unassigned by windows ... then

(1) Ubuntu can be installed on the "blank" partition without affecting the XP boot loader.
(2) Maybe installed on NTFS -- but why bother -- it is easier to leave the extra space unassigned by win/dos.

SO say I have 80 GB of a 250drive unassigned at the end, when I load the Ubuntu install, it will see the unassigned space at the end, I can pick it, and it will install in there -- which is how other linuxes worked.

Now how do I change the XP boot loader -- BTW -- I have done this manually many times, but you will recall that the entries in the BOOT.INI refer to partitions that windows or DOS recognizes.  I have not seen reference to a partition that has not been assigned a logical volume -- for example, the typical XP loader specifies --

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" 

if you speicfy multi(0)disk(0)rdisk(0)partition(5)  .. what do you put after it, if there is no partition recognized by the XP boot loader?

---

### Post by BaffledMollusc on 2007-04-21
> **new_user10 said:**
> Thanks for the individual point-by-point answers, that helps a lot.

So if the partition was (1) NTFS or better still (2) space left unassigned by windows ... then

(1) Ubuntu can be installed on the "blank" partition without affecting the XP boot loader.
(2) Maybe installed on NTFS -- but why bother -- it is easier to leave the extra space unassigned by win/dos.

SO say I have 80 GB of a 250drive unassigned at the end, when I load the Ubuntu install, it will see the unassigned space at the end, I can pick it, and it will install in there -- which is how other linuxes worked.

Yes, that will work.
> 
Now how do I change the XP boot loader -- BTW -- I have done this manually many times, but you will recall that the entries in the BOOT.INI refer to partitions that windows or DOS recognizes.  I have not seen reference to a partition that has not been assigned a logical volume -- for example, the typical XP loader specifies --

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" 

if you speicfy multi(0)disk(0)rdisk(0)partition(5)  .. what do you put after it, if there is no partition recognized by the XP boot loader?
I don't know anything about the XP boot loader, I'm afraid.

---

### Post by louieb on 2007-04-22
Linux won't in install on NTFS either. Just a guess but probably has something to do with it not be Open Source. And the code is owned by the 800 pound gorilla that is Microsoft.

Look at post #2 of this thread [http://ubuntuforums.org/showthread.php?t=351692](http://ubuntuforums.org/showthread.php?t=351692) 
He explains how he boots Linux on an extended partition using NTLDR. 
The short of it is:[LIST]
[*]Install Grub in the boot sector of the Linux partition.
[*]Make a copy of the boot sector
[*]Copy this file over to your windows operating system
[*]Modify the boot.ini file.[/LIST]If you decided to try Linux get yourself a decent Live CD. I recommend Puppy or Koppinx. The Ubuntu Live CD is not good for much other that installing Ubuntu. A live CD is what you will need to make the copy of the boot sector.

---

### Post by new_user10 on 2007-04-22
Thanks Louieb -- your points made PERFECT sense to me, since all of XP boot loader depends on getting the right boot sector for the OS you want to run, and swapping in and out that bootsector for each OS loading.

I don't suppose you get points for your input on this forum, but if you do, you deserve the MAX for such clear help !!

---

