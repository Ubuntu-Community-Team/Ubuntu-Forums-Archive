---
title: "Trying to find a viable storage solution for my Ubuntu/Windows dual boot"
date: 2014-10-23
forum: Installation &amp; Upgrades
---

### Post by robbarton27 on 2014-10-23
Hey guys;

Trying to find a viable storage solution for my Ubuntu/Windows dual boot.

I have:

120gb SSD
1tb HDD
60gb SSD


I plan to run Ubuntu for software and web development and Windows for gaming and Netflix, but I would like to also do some development on Windows. Here is the solution I have came up with:

**120gb SSD - **
Windows 8.1 and programs files

**60gb SSD -** 
Ubuntu and /home/

**1tb HDD - **
[LIST]
[*]partition 1 (750gb): Games, music, videos, documents, other personal documents etc 
[*]Partition 2 (250gb): Development projects 
[/LIST]

My question is, how can I ensure that I can read and write to the 250gb partition on both Windows and Ubuntu? I would like to access my development projects on both OS's. If I partition it as an NTFS partition, will any issues arise? I seem to be getting mixed answers on my research.

Thanks.

---

### Post by Bucky Ball on 2014-10-23
> **robbarton27 said:**
> If I partition it as an NTFS partition, will any issues arise? I seem to be getting mixed answers on my research.

Welcome. No. That is the way it is generally done for sharing data between Win and Ubuntu.

My two cents: I would go for Win and Ubuntu on the 60Gb SSD and keep all data on another disk. The trick with the Ubuntu install is to have /home directory, no separate /home partition, and create symlinks inside the /home directory that link to the data on another disk, e.g. /home/user/Videos is actually a symlink to /mnt/data/Videos which is another partition on another disk.;)

Doing it this way you only need 20Gb or so for Ubuntu as no personal data is stored in the OS partition. Leaves you with 120Gb super-fast storage and the 1Tb hard drive.

Having said all this, some folk here prefer to have OSs on separate disks where possible, as you were planning ...

---

### Post by fantab on 2014-10-23
> **robbarton27 said:**
> Hey guys;

Trying to find a viable storage solution for my Ubuntu/Windows dual boot.

I have:

120gb SSD
1tb HDD
60gb SSD


I plan to run Ubuntu for software and web development and Windows for gaming and Netflix, but I would like to also do some development on Windows. Here is the solution I have came up with:

**120gb SSD - **
Windows 8.1 and programs files

**60gb SSD -** 
Ubuntu and /home/

**1tb HDD - **
[LIST]
[*]partition 1 (750gb): Games, music, videos, documents, other personal documents etc
[*]Partition 2 (250gb): Development projects
[/LIST]

My question is, how can I ensure that I can read and write to the 250gb partition on both Windows and Ubuntu? I would like to access my development projects on both OS's. If I partition it as an NTFS partition, will any issues arise? I seem to be getting mixed answers on my research.

Thanks.

If you are dual-booting two different OS and if you have more than one HDD/SSD then its a good idea to keep the OS's on separate HDD/SSD.
I suggest that you also keep a small SWAP (2-4gb) partition on the Ubuntu ssd. No need to make a separate /home partition.

It is safe to use NTFS shared partition between Windows and Ubuntu. Ubuntu uses a 'ntfs_3g' driver to read and write to NTFS.

When installing Ubuntu make sure you install the boot-loader [Grub] on the same SSD on which you're installing Ubuntu; By default boot-loader will be installed on the first HDD/SSD or /dev/sda. 
Then in your BIOS/UEFI menu change the HDD boot order to boot Ubuntu SSD first.. That should keep both your OS's completely separate. You can boot both Win and ubuntu from Grub.

---

### Post by oldfred on 2014-10-23
I prefer each system on a separate drive and each configured to only boot from that drive. And then mount data partitions separately and use the links as suggested by Bucky Ball.

But with Windows 8 you must make sure hibernation or fast boot is off.

 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
Force removal of hiberfil from Ubuntu

---

