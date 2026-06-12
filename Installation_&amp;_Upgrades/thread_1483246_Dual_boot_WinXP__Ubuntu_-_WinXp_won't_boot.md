---
title: "Dual boot WinXP / Ubuntu - WinXp won't boot"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by CuddlyPanda on 2010-05-14
Hi,
Just upgraded Ubuntu 09-10 to 10.04LTS using update manager. During the update, GRUB gave list of devices and partitions and asked to select where to install..Since no help as to proper device and said if in doubt select all.. I selected both devices as well as some partitions.. On rebooting PC, i got GRUB with selection of Ubuntu and Windows XP Professional. While selecting Ubuntu boots OK, selecting WinXP, goes to blank screen with flashing cursor and hangs:(.  I found that my BIOS no longer sees my HDD's:confused: .  
I tried  sudo grub-install /dev/sda (location of winXP) but got this error message: cannot find a device for /boot/grub (is /dev mounted?)  Howerver when in Ubuntu I can see both drives and all their partitions except for the linux partitions.

Help to get BIOS to recognize the HDD's and winXp running would be hugely appreciated.  Thx

---

### Post by darkod on 2010-05-14
Selecting partitions too for grub was the mistake. Grub is a bootloader and bootloaders go to the Master Boot Record of a disk, not on partitions.

If that is your only problem, the fix is here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Since you can boot ubuntu, you can do it from there. Or from live mode when booted with Try Ubuntu option.

If you are unsure which is your XP partition, ask first. But the grub menu is showing it for you, for example Windows XP on /dev/sda1. That means you have to fix partition #1 on the disk /dev/sda.

I don't understand why you think BIOS is not seeing the hdd. If that was the case, you wouldn't be able to boot any OS.

Lets see if the fix solves it, and then whether there are other problems.

---

### Post by CuddlyPanda on 2010-05-14
Thx ur Replay Darko

I cant use the WInXP CD to restore (R). When I used WinXP CD to restore (R) fixboot or fixMBR i got error message that devices  did not exist. I then went to BIOS that tolds me no devices installed... 

However, I still see both HHD in Ubuntu file browser as well as when using Sudo fdisk  -l  .. Since i can see the HDD structure and files.. i understand that HDD are  intact as follows:

Dev/sda :  160GB
Dev/sda1: C: Primary Partition of 5GB (NTFS) for pagefile (moved to dev/sdb1), boot.ini. ntldr, and other system files; 
dev/sda2:  Extended partition (159GB)
dev/sda5:  D: logical of 125GB for WInXP (NTFS);
dev/sda6:  E: logical of 22GB for data  (NTFS)

Dev/sdb :  80GB
dev/sdb1:  F: Primary Partition (NTSF) - contains pagefile.sys for winXP
dev/sdb2:  Extended partition
dev/sdb5:  /root for Ubuntu (ext4) of 32GB
dev/sdb6:  /home (ext4) of 32GB
dev/sdb7:  swap for ubuntu
dev/sdb8:  G: logical of 6GB for data (NTFS)

Am i correct that the partition to be fixed should be C:\  and not D:| where winXP is installed? Seems pointer to the win bootloader is broken?  Is testdisk my best option to fix?

Thx

---

### Post by darkod on 2010-05-14
Yes, use the fix in that link to repair /dev/sda1. Usually that is enough.

---

### Post by goldshirt9 on 2010-05-14
cheers for the link, i was looking for that

---

### Post by CuddlyPanda on 2010-05-14
testdisk worked great  thank you so much ur help

---

