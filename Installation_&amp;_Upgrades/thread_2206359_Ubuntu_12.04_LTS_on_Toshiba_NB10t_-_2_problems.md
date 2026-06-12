---
title: "Ubuntu 12.04 LTS on Toshiba NB10t - 2 problems"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by jamesp2 on 2014-02-18
Have been trying to install Ubuntu for the last few days alongside preinstalled Windows8.

Windows partition manager gives me the following

[ATTACH=CONFIG]250468[/ATTACH]

I'm trying to install ubuntu into the unallocated space - get the following error at installation - "no root system file defined" when am trying to custom install.

Should i delete any partitions and how can i get ubuntu into the unallocated space?
Many thanks

James

---

### Post by ajgreeny on 2014-02-18
If "custom install" means you're using the "Something else" option you must remember to select one partition as ext4, set mountpoint / (that is the missing root partition), and select the Format tick box.  Your error sounds as if you are missing one of those requirements when you install.

---

### Post by Bucky Ball on 2014-02-18
You have the disk set to EFI which means Win is installed in EFI which means you MUST install Ubuntu in EFI.

You need to go to the BIOS and switch off fastboot, secureboot, boot into Win and switch off 'faststart' in the software (may be called something slightly diff) then try again. To change faststart, see [HERE.]("Change Win8 UEFI settings from OS: http://www.pcmag.com/article2/0,2817,2417361,00.asp")

For a better understanding of UEFI, see resident install/booting guru oldfred's explanation here, post 22: 
[http://ubuntuforums.org/showthread.php?t=2197982&page=3&p=12894031#post12894031](http://ubuntuforums.org/showthread.php?t=2197982&page=3&p=12894031#post12894031)

... and here is some further reading from oldfred and others:

oldfred's tips:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Managing Everything UEFI:
[http://www.rodsbooks.com/efi-bootloaders/index.html](http://www.rodsbooks.com/efi-bootloaders/index.html)

EFI Bootloader Installation:
[http://www.rodsbooks.com/efi-bootloaders/installation.html](http://www.rodsbooks.com/efi-bootloaders/installation.html)

A Quick Installation Guide:
[http://www.rodsbooks.com/linux-uefi/#preparing](http://www.rodsbooks.com/linux-uefi/#preparing)

The quick installation guide will give you an idea. The situation with installing Ubuntu in EFI continues to improve but still need to jump through some hoops on occasion. ;)

---

### Post by jamesp2 on 2014-02-18
Thanks for the replies.
Here is the screen shot from gparted.

Still getting the same warning when trying to install - no root system file defined

In the bios there is no option to switch off EFI and go through CSM/legacy boot.

---

### Post by Bucky Ball on 2014-02-18
> **jamesp2 said:**
> 
In the bios there is no option to switch off EFI and go through CSM/legacy boot.

Repeat: You do NOT want to switch off EFI anyway as it looks like Win is installed in EFI (that FAT partition is the EFI partition). If you switch off EFI and change the disk to legacy that will prevent Win from booting at all. If you install Ubuntu in legacy you will need to get Boot Repair to transform it to an EFI install to get Win booting and this is not the way to go.

---

### Post by jamesp2 on 2014-02-18
Errrrrr.......OK
Pretty confused now....but thanks.
How from where I am can I install Ubuntu?

---

### Post by Bucky Ball on 2014-02-18
> **Bucky Ball said:**
> You have the disk set to EFI which means Win is installed in EFI which means you MUST install Ubuntu in EFI.

You need to go to the BIOS and switch off fastboot, secureboot, boot into Win and switch off 'faststart' in the software (may be called something slightly diff) then try again. To change faststart, see [HERE.]("Change Win8 UEFI settings from OS: http://www.pcmag.com/article2/0,2817,2417361,00.asp")



Start here. Refer to the links in my last post.

---

### Post by jamesp2 on 2014-02-18
Thanks. Will go step by step.

---

