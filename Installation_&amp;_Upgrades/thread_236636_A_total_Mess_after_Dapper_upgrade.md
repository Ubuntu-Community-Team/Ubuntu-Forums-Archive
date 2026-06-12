---
title: "A total Mess after Dapper upgrade"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by bootbat on 2006-08-15
Hi....

I triple booted my system today with Ubuntu Breezy Badger 5.10. I now have Ubuntu and XP on a single hard drive and FC 5 on another. Here's my fdisk -l:

> [root@bootbat ~]# fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2435    19559106    7  HPFS/NTFS
/dev/sda2            2436        4779    18828180   83  Linux
/dev/sda3            4780        4870      730957+   5  Extended
/dev/sda5            4780        4870      730926   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14        4865    38973690   8e  Linux LVM

Everything went fine till I decided to upgrade to Dapper 6.06....I followed the instructions in [https://help.ubuntu.com/community/DapperUpgrades.....After](https://help.ubuntu.com/community/DapperUpgrades.....After) all files were downloaded successfully, it started unpacking and updating..All seemed to go fine but without reason my computer restarted in the middle of it all. when I went to Ubuntu, it seemed that it loaded fine, took me to the login screen. After I logged in, all it gave me is a brown screen and a mouse with nothing at all. I waited for about an hour thinking it must be doing something....but it is still there..I am logged in to FC5 now and posting this...I wanted to try Ubuntu for a long time after all things I heard about it from my friends. 

I will really appreciate any help to restore my Ubuntu back. I do not want to reinstall it again as configuring grub to triple boot took a lot of effort and time. Please give me any pointers. I am new to Ubuntu (and Debian Linux) and do not know much to resolve this.

Thank you all!!

---

### Post by linear on 2006-08-15
From the login screen, you should be able to get to a shell (one of the "Session" choices - afraid I don't recall the exact sequence), at which point you can start troubleshooting.

If the installation failed to complete, you could start by looking for and fixing broken dependencies (this should then allow you to complete installation). The instructions [here]("http://www.ubuntuforums.org/showthread.php?t=186672") are very useful.

---

