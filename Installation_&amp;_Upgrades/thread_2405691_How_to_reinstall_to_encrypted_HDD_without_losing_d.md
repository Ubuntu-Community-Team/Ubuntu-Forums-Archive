---
title: "How to reinstall to encrypted HDD without losing data?"
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by MoebusNet on 2018-11-09
Google hasn't been a friend for this one. Lubuntu 18.04.1 64-bit installation with encrypted HDD selected. The 'Backups' application has quit working for me, and one of the options I've been looking at has been to do a reinstallation of Lubuntu 18.04.1. HOWEVER, I have not been able to find any way to reinstall without erasing all my data, applications, etc. In previous *buntu versions with an unencrypted HDD and a separate /home partition, reinstallation was quite straightforward. I do have other backups (Grsync) but a clean installation with having to reinstall all of the applications is looking like the 'nuclear option'; I would prefer to preserve my apps and data if possible.

It appears that the articles written about reinstallation and encryption all predate Ubuntu's default encryption option now of full-disk encryption. Where can I find a guide to this type of reinstallation? Lubuntu is reporting 'No operating system detected' when it examines my HDD, because the drive is encrypted. It therefore does not offer a 'Reinstall Lubuntu' option - only 'erase HDD and install Lubuntu'.

---

### Post by TheFu on 2018-11-09
**aptik** will backup user data and the list of installed packages.  I don't know if it works on 18.04.

You can backup anything on an unlocked, running, system using any backup tool you like.  I use **rdiff-backup** to get the parts of a system that are settings, manually installed tools outside the pkg manager, data and some other places with stuff like crontabs, manually installed package lists, disk partition layouts, lvm configs, RAID configs, and other system settings so those can be easily put back at restore.  **lsblk, lvs, vgs, pvs, fdisk**, and **apt-mark** are the main tools besides rdiff-backup.  If MariaDB is on the machine, I use the sqldump tool as well to ensure a clean DB backup is captured.  The script that does DB backups is posted in these forums too.

I retain between 60 days and 180 days of versioned backups for each system. How much depends on the risk factors for the system.  Efficient versioned backups is mandatory.  I was burned in the early 2000s and lost a bunch of data.  To me, the data is critical, the OS isn't a big deal.  I can put it back fairly easily in 30-45min.

I use full disk encryption on all my portable systems.  The detailed steps for recovery using my method is posted in these forums too. Took me about 4-5 restore attempts before I got everything necessary.  I do NOT backup the entire OS.  
The restore process begins by installing the same OS release that was on the machine and the ssh server with rdiff-backup.  That takes about 10-15 minutes, then another 15-30 minutes to restore the data and settings and install the packages the apt-mark tool provided pre-backup.

The only trick for the storage aspects is that the directories need to appear to be in the same place they were before.  Everything underneath - encryption or not, LVM or not, RAID or not, doesn't matter, provided the unlocked disks and directories appear in the correct locations.

If you want a 1-click restore, then you are going to need a huge amount of storage. I don't know of any tool that can do versioned backups above the encrypted storage (raw disks) in an efficient way.

I stopped using the old encrypted HOME directory setup because making unattended system backups wasn't working. Haven't had the same issue with FDE. The backups are really separate from the encryption, completely.

Hopefully, someone else will respond with some other options.  As usual, there are 50-500 solutions to this problem.

---

