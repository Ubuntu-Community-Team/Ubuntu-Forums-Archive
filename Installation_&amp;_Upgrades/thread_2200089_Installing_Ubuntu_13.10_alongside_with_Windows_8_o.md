---
title: "Installing Ubuntu 13.10 alongside with Windows 8 on a 64 Gb SDD"
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by jnaphta on 2014-01-17
Hello!

I have been using Ubuntu for more than 5 years in my old computer. Now that I am buying a new machine, I would like to keep my favorite OS on it. But the main reason for the change is that I am going to use Windows 8 for video editing. So I will have to fresh install both Windows and Ubuntu. I will buy a 64 Gb SSD just for the OS, and use bigger HDDs for data. So I have two big questions:

1. What would be an optimal partition of the SSD for both systems? How much space should I allocate for Ubuntu? Knowing that Ubuntu is my system for daily uses (internet, mail, watching video, music, bureaucratic...) and that windows will only be used for video edition. My experience tells me that Ubuntu does not need a lot, but I have no idea of what are the needs of windows 8.

2. Would it be possible to locate ubuntu's /home directory in the HDD to which windows will also have acces? And even to make of the /documents folder in Ubuntu and My documents in windows one and the same folder? 

And the last question: most of the threads concerning windows 8 and ubuntu talk about PCs with win8 preinstalled and the UEFI problem. I understand that if I install both (first win8, then ubuntu) it will be as easy as with the previous versions of windows. Is there any official guide for installing together these two operating systems? I have only found threads dealing with the UEFI problem.

Thanks a lot for your help!

---

### Post by tfrue on 2014-01-17
Yes, there are tons of walk throughs. Here is a link:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Here is my opinion, to fully optimize your video editing you will want to save your files and utilize the cache of the SSD to help the video editing program. I know Adobe After Effects can utilize the cache, but if that's not an issues then don't worry about it. Knowing how data hungry Window's can get, I would give it at least 20GB. 

Window's is not compatible with ext4 FS, so you will not be able to read the data from Window's but you can read Win data from Ubuntu. I wouldn't mix the partitions simply because they are two different OS using different File Systems, so no. 

I would install Win 8 first, then use Disk Manager in Win to partition the disk estimating how much you want for Win, whether that be just for booting or storage, then live boot into Ubuntu and install with "Something Else" and you should be on your way.

The main thing I would say that you need to be on the lookout for when you are installing Ubuntu is to make sure that you are going to use EFI or BIOS (GPT/MBR). If Win 8 is going to be installed to a GPT disk, then make sure that you live boot with EFI so you don't make a big mess.

You can make the SSD a boot only device, and mount the data partitions of both Win and Linux in different partitions on your HDDs. There are benefits, but I don't have to worry about it now as I have a 500GB HDD with about 300GB free, so I don't go too crazy with my partitioning. 

Good luck,
Chris

---

### Post by fantab on 2014-01-17
If I were you, I would install both OS on the SSD. Windows like to see the C: partition with a minimum of 30% free space (after installing everything you want to) for an optimal performance. Video editing sofware generally take up lots of space... with only 64Gb SSD you might be cramped for space installing both OS there. If its feasible then go for a bigger SSD than what you have in mind.

Newer machines will have UEFI, and UEFI only works from a GPT formatted HDD... from GPT you will need a separate 300Mb EFI System Partition.

64Gb SSD:
300Mb FAT32 EFI flag=boot
40+Gb NTFS Windows C\:
20Gb Ext4 Ubuntu /


On HDD:
To share a partition/DATA between Windows and ubuntu you need to have a NTFS data partition. Windows will NOT work with Linux partitions but Linux can work with NTFS partitions.

My two cents....

---

### Post by jnaphta on 2014-01-18
Thanks a lot for your answers!

> 64Gb SSD:
300Mb FAT32 EFI flag=boot
40+Gb NTFS Windows C\:
20Gb Ext4 Ubuntu /

Supposing that I buy a 128Gb SSD, should I just use 20Gb for Ubuntu and the rest for Windows and the EFI partition? Does Ubuntu need more than that for daily uses?

> On HDD:
To share a partition/DATA between Windows and ubuntu you need to have a  NTFS data partition. Windows will NOT work with Linux partitions but  Linux can work with NTFS partitions.

I would prefer to share because I cannot preview which amount of data I am going to use with each system. No doubt it will be more with Windows but I already have a 320Gb and growing HDD full of files that I use with Ubuntu... but that I may need in windows too. So what would be the risk if I put my /home directory into a windows NTFS data partition? I have already had a laptop running with two partitions and know that Ubuntu can acces to the other one, but I just find it quite annoying to have to reorganize the whole when one partition becomes full... but according to @tfrue it is not a good idea. It would just be for my convenience, but I will not dare if it is somehow risky.

Thanks again!

---

### Post by Bucky Ball on 2014-01-18
> **jnaphta said:**
> 
And the last question: most of the threads concerning windows 8 and ubuntu talk about PCs with win8 preinstalled and the UEFI problem. I understand that if I install both (first win8, then ubuntu) it will be as easy as with the previous versions of windows. Is there any official guide for installing together these two operating systems? I have only found threads dealing with the UEFI problem.

If Windows 8 is pre-installed it will be installed EFI. That means you must install Ubuntu EFI also. Your only other option is to boot Win8, burn the recovery disks so you can reinstall, switch EFI off in your BIOS then install Win followed by Ubuntu as per normal.

Installing Ubuntu in EFI: Switch off fastboot and secureboot in the BIOS. Boot into Win8 and disable faststart. Install Ubuntu in EFI. It will automagically see the EFI partition used by Win8 and install grub to that. You must partition manually by using 'Something Else' at the partitioning section of the install (safest). That is a VERY basic explanation. ;)

---

### Post by fantab on 2014-01-18
> **jnaphta said:**
> Thanks a lot for your answers!



Supposing that I buy a 128Gb SSD, should I just use 20Gb for Ubuntu and the rest for Windows and the EFI partition? Does Ubuntu need more than that for daily uses?



I would prefer to share because I cannot preview which amount of data I am going to use with each system. No doubt it will be more with Windows but I already have a 320Gb and growing HDD full of files that I use with Ubuntu... but that I may need in windows too. So what would be the risk if I put my /home directory into a windows NTFS data partition? I have already had a laptop running with two partitions and know that Ubuntu can acces to the other one, but I just find it quite annoying to have to reorganize the whole when one partition becomes full... but according to @tfrue it is not a good idea. It would just be for my convenience, but I will not dare if it is somehow risky.

Thanks again!

If you get a 128Gb SSD then 100Gb for Windows and the rest for Ubuntu.
NO. don't use NTFS for Ubuntu /home. Have a /home on the HDD.

---

### Post by oldfred on 2014-01-18
Ubuntu system partitions including /home must be Linux formatted, but you can in effect split /home into the mostly hidden user settings and have data linked back into /home from data partition(s). I have two data partitions, one NTFS from when using XP and one Linux formatted. Since not using XP anymore new data goes into my Linux partition, but I have not converted data from NTFS partition yet.

You also have to be careful not to use the always on hibernation or fast boot in Windows. It may also mount the data partition and you will lose the data you write from Ubuntu.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) with total 11GB used. Backup of /home still vital.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

