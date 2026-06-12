---
title: "Dual boot with an Archlinux OS"
date: 2018-04-22
forum: Installation &amp; Upgrades
---

### Post by geert2 on 2018-04-22
I'm trying to install Ubuntu alongside my Archlinux OS. I have 20 Gb of free space. When I start the installation process, I get a message telling me that no operation systems where detected. My only options are either to erase my hard disk, or to choose 'Something else'. Why is my OS not detected? When I choose the 'Something else' option my GPT partitions are recognized. When I want to create a partition in the free space I'm asked to create an primary or a logical partition. This confuses me because I thought that whit GPT I no longer have to choose between primary and logical.

---

### Post by yancek on 2018-04-22
Can you boot the Ubuntu media?  If so, open a terminal and run this command and post the output here:

> sudo parted -l

Are you booting the Ubuntu medea in EFI or Legacy?  Take a look at the link below, official Ubuntu documentation.  If you scroll down the age a bit, you will see a section named "Identifying if computer boots Ubuntu UEFI.  Make sure you are booting UEFI if ARch is UEFI, Legacy if it is Legacy.

    [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-04-22
The most common reason for not correctly seeing Windows is that you have not turned off fast start up which is really just hibernation. The Linux NTFS driver will not mount NTFS partitions that are hibernated to prevent damage.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

But there are multiple other reasons. Like you have drive set for RAID, not AHCI, drive was gpt and converted to MBR, errors on drive, drive converted to dynamic partitions from basic which never should be done even if just running Windows.

While it is true that gpt only has one type of partition, the installer still seems to ask the question when creating partition. Just say primary if using gpt. I think even if you say logical it will not be a logical partition, anyway if drive is gpt.

---

