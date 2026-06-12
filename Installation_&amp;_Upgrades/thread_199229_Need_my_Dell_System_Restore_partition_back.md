---
title: "Need my Dell System Restore partition back"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by crashtest on 2006-06-18
I just bought a new Dell Inspiron 9400 with Go 7900 Nvidia card, and installed Dapper in a dual-boot configuration with XP using the Live CD install.  The live installer overwrites the MBR but I know the original Dell system restore partition os still on the drive.  

The notebook has developed a hardware problem on day 2 - it overheats and the hard drive stops working.  I can run the notebook for a couple of hours before this occurs, so I now want to put it back to factory default setup before contacting Dell for support.  

(By the way - Ubuntu installs and works _perfectly_ on this notebook, so it's a real shame about the overheating issue)

Two questions:
1. What do i have to put in the grub configuration to get the system restore partition to boot?
2. Will the system restore write across the whole drive and delete the Linux partions, thus giving me the factory setup back?

The current partion scheme is as follows:

/dev/sda1 vfat 47 MB (The Dell diagnostics partition)
/dev/sda2 ntfs 22GB Windows XP
/dev/sda3 vfat 3 GB Dell System Restore
/dev/sda5 vfat 5 GB (for sharing files between Win and Linux)
/dev/sda6 ext3 23 GB /
/dev/sda7 swap 1GB

The grub boot loader offers these choices on boot-up:

Ubuntu, kernel 2.6.15.25-386
Ubuntu, kernel 2.6.15-25-386 (Recovery Mode)
Ubuntu, kernel 2.6.15-23-386
Ubuntu, kernel 2.6.15-23-386 (Recovery Mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Home Edition

Any help would be appreciated.

---

### Post by H.E. Pennypacker on 2006-07-30
> 1. What do i have to put in the grub configuration to get the system restore partition to boot?

You don't have to do anything with GRUB in order to restore your copy of Windows to its original state.  Dell has programmed a key that you press while the system is loading in order for you to access the Dell restore partition.  The restore partition will then override the current Windows partition, and then put everything back to its original state.

> 2. Will the system restore write across the whole drive and delete the Linux partions, thus giving me the factory setup back?

The restore process will cover the Windows partition, replacing the Windows partition with what was there originally.  It shoudl not have any effect on a Linux partition, but it will likely dump GRUB.  You will then, when the process has completed, restore GRUB.

There is more extensive information [available here]("http://www.goodells.net/dellrestore/index.htm").  It would be in your interest to read all that information.  It may take a while.

---

