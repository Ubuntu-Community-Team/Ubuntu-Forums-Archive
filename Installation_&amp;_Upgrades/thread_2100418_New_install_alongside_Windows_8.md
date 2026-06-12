---
title: "New install alongside Windows 8"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by Binabik666 on 2013-01-01
New Acer AX1470 - burned a cd & DVD & USB stick

Followed instructions for each to boot into Ubuntu 12.12

Get screen showing "Choose an Operating System: with the choice of Windows8 or Ubuntu

Of course I choose Ubuntu

It sends me to a DOS screen with: "Windows Boot Manager"

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem: it next gives the standard Windows fix problem with 3 items to follow

FILE: \ubuntu\winboot\wubildr.mbr
STATUS: 0xc000007b

Info: The application or operating system couldn't be loaded because a required file is missing or contains errors

This screen lasts about 20 seconds then shuts down the computer

I have been at this for a while & figure I need help to get into Ubuntu

I have been using Ubuntu for about 5 years & have not experienced a problem in the past - all upgrades new installs have been painless

---

### Post by oldfred on 2013-01-01
It seems like you are installing wubi. Wubi does not work with gpt partitions and new installs of Windows 8 use UEFI and gpt partitions.

---

### Post by Binabik666 on 2013-01-01
After much reading & frustration realized it is a conflict with Windoze8 - put my boot disk in a Vista box & no problem -  just like it was suppose to do

Will use the windows8 for my business programs & the Vista as my Ubuntu main computer

It was an exciting 24 hours

---

### Post by oldfred on 2013-01-01
If you want to install with Windows 8 it can be done. And with gpt partitions the old 4 primary partition limit is gone. But secure boot is the new issue. And grub has a bug or two still that Boot-Repair can work around.

Ubuntu's 64 bit version of 12.10 has grub2 2.00 that works with secure boot. 

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

