---
title: "Dual-booting with two hard drives? Help...?"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Rune21 on 2009-12-06
Alright, so I'm trying to install Ubuntu to a computer with Windows XP already installed on it. However, the computer has two physical hard drives connected. One does not have XP on it, I don't think. Everything I've found about setting it up to Dual-boot with two hard drives talks about putting the OS's on the two separate hard drives, but I want to put Ubuntu on the XP hard drive and let it dualboot both OS's from the same drive, keeping the larger drive for storage. 

Yet, Ubuntu's Installation always detects the Storage Hard drive. I don't know how to get it to detect the C drive instead. Help please...?

---

### Post by darkod on 2009-12-06
There are few points to note. First of all, if the XP drive has partitions created on the whole drive, it can't be used to install except unless XP is shrinked. It need to have unallocated space, not belonging to ntfs partition.
Also, some drives that have raid settings remains can't show up in ubuntu. If you are not running raid you can check this by booting with ubuntu cd, selecting Try Ubuntu and when it loads open terminal (Applications-Accessories) and execute:
sudo apt-get remove dmraid

See if it can recognize the hdd after that. Also while you are booted with the ubuntu cd you can open Gparted (System-Administration) and take a look at both drives partitions.

---

### Post by presence1960 on 2009-12-06
> **darkod said:**
> There are few points to note. First of all, if the XP drive has partitions created on the whole drive, it can't be used to install except unless XP is shrinked. It need to have unallocated space, not belonging to ntfs partition.
Also, some drives that have raid settings remains can't show up in ubuntu. If you are not running raid you can check this by booting with ubuntu cd, selecting Try Ubuntu and when it loads open terminal (Applications-Accessories) and execute:
sudo apt-get remove dmraid

See if it can recognize the hdd after that. Also while you are booted with the ubuntu cd you can open Gparted (System-Administration) and take a look at both drives partitions.

+1

You need to shrink XP's partition to create room for Ubuntu. You can use the Ubuntu Live CD to do so. Boot the Live Cd and at the menu choose "Try ubuntu without any changes to your computer." When the desktop loads you can go System > Administration > Gparted (in 9.10) or Partition Editor (in 9.04 or less). Choose the disk with windows from the upper right drop down box. Right click the XP partition and choose Resize/Move. Set the parameters to shrink XP. When ready click apply. It may take some time do not interrupt the process or your partition may become corrupt or even unusable.

I would suggest you defrag Windows at least once, probably twice and disable hiberbation & system restore prior to resizing XP. Once complete install Ubuntu. When you go back to windows you can enable system restore & hibernation.

---

### Post by Rune21 on 2009-12-06
Resolved. I managed to work out how to install it through windows...

---

