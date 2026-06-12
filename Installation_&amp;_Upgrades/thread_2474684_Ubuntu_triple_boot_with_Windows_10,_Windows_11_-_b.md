---
title: "Ubuntu triple boot with Windows 10, Windows 11 - boot loader"
date: 2022-05-05
forum: Installation &amp; Upgrades
---

### Post by lsepolis123 on 2022-05-05
[COLOR=#000000][FONT=Calibri]Linux triple boot system, boot loader where…[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]I had Windows 10, and dual boot set it up with Windows 11, now wanted to set it as triple boot system with Ubuntu 22.04, but the only problem on this, is at the end of Ubuntu installation if says about boot loader and which partition to install, what have to choose in this case?[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] [/FONT][/COLOR]

---

### Post by yancek on 2022-05-05
The default selection should work and on an older Legacy system would usually be /dev/sda, that is if you have a standard drive.  If you have an SSD the name will be different.  On an EFI install, if you booted and installed Ubuntu in UEFI mode, it should create an ubuntu directory in the EFI partition which should already exist with your windows installs by selecting the default option.

---

### Post by grahammechanical on 2022-05-05
My system is UEFI and i have an ssd. I recently installed 22.04 as a dual boot with 20.04. The 22.04 installer choose sda as the default location for the boot loader. I changed it to the existing EFI system partition by pulling up the drop down menu. Everything worked fine.

Regards

---

### Post by lsepolis123 on 2022-05-07
> **yancek said:**
> The default selection should work and on an older Legacy system would usually be /dev/sda, that is if you have a standard drive. 

Yes, I have Standard HDD. So, select the default location, for boot loader in this case, OK

BTW, 

AFTER install Ubuntu or an Ubuntu Flavor, the Default Boot OS should become the Ubuntu... the last installed OS? 

And also, the select OS screen during boot should become from Blue of W10/W11, to a black screen of Linux OS (Ubuntu) to select from w11, w10, Ubuntu boot from?

Before install Ubuntu OS as triple boot, should create a partition for this, from Windows Disk Management, correct?

---

### Post by yancek on 2022-05-07
>  Before install Ubuntu OS as triple boot, should create a partition for this, from Windows Disk Management, correct? 		

No.  Much simpler to just shrink the largest windows partition from windows Disk Management and leave unallocated space for Ubuntu.  After doing this, reboot into windows and run chkdsk to ensure windows still boots withot errors.  You need to create a linux filesystem on the partition for Ubuntu and can't do that from a default windows so do it from the Ubuntu installer.

If you install the Ubuntu Grub bootloader to the MBR (this should be the default) you should then see the Grub boot menu.

When you install a windows OS, the newer one usually overwrites the older entry so you may see a menu for windows 11 which will also have windows 10.  Haven't used 11 so I'm not sure this still applies.

---

### Post by lsepolis123 on 2022-05-08
[IMG]https://1drv.ms/u/s!Aty5ebD9Y5-uiO9ppoBxOUbwv_wfxQ?e=sYf7eL[/IMG]Tried Install Ubuntu Studio 22.04 but failed and give up... see shot:... too slow...

[https://1drv.ms/u/s!Aty5ebD9Y5-uiO9ppoBxOUbwv_wfxQ?e=sYf7eL](https://1drv.ms/u/s!Aty5ebD9Y5-uiO9ppoBxOUbwv_wfxQ?e=sYf7eL)

Now I will try Ubuntu Mate 22.04...
[IMG]https://1drv.ms/u/s!Aty5ebD9Y5-uiO9ppoBxOUbwv_wfxQ?e=sYf7eL[/IMG]

---

### Post by lsepolis123 on 2022-05-08
What is the easiest way to install Next Cloud in Ubuntu 22.04 probably Ubuntu Server...for local network usage and experiment in a 12-years old PC...??? Is any Ubuntu Flavor having intergraded Next Cloud... for x86-64 PC...?

---

