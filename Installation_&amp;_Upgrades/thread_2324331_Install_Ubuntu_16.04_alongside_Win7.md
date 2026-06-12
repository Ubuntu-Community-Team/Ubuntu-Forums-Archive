---
title: "Install Ubuntu 16.04 alongside Win7?"
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by Desert_Outlaw on 2016-05-12
grahammechanical: I am trying to install 16.04 on a HP laptop with Windows 7 yet everything I find only shows side by side installation for Windows 8 and 10. Does that imply I need to install 14 or 15 first and then wait for possible updates?  The present 16.04 install does not recognize the new petition (which is healthy) for installation and delivers a root error if attempted. Its appears as if Windows 7 is not an option for side by side installation or else the developers are becoming like M$ and rushing beta versions out as releases.

Thanx!

---

### Post by vasa1 on 2016-05-12
This post was moved from [http://ubuntuforums.org/showthread.php?t=2324153](http://ubuntuforums.org/showthread.php?t=2324153) because it is about installation as opposed to upgrading.

@Desert_Outlaw, it's preferable to start a new thread for your issue rather than post in a thread started on another issue. It helps all concerned.

Thanks.

---

### Post by grahammechanical on 2016-05-12
Let us think about the fundamental difference between machines with Windows 7 pre-installed and machines with Windows 8 or 10 pre-installed. The Windows 7 machine will have a BIOS boot system with MBR partitioning & the Windows 8/10 machine will have a UEFI boot system with GPT partitioning. Why is this important in your case?

With MBR partitioning we are only allowed a maximum of 4 primary partitions. With GPT partitioning we can have a much, much larger number of partitions. If you already have 4 primary partitions on that hard disk then it is not possible to create the minimum of 2 partitions that Ubuntu needs. For this reason the installer does not offer an Install Alongside option.

You need to open a Windows utility that shows you the partition layout of the hard disk and take a screen shot of the partition layout and post it in this thread. Then we can see for ourselves and give accurate advice.

> The present 16.04 install does not recognize the new petition (which is healthy) for installation

This  situation has been present since I first installed Ubuntu back in 2007.

What you need is  unallocated space and only three primary partitions. Then the installer  can make use of the remaining 4th allocation of a primary partition and  use it to create out of the unallocated space a special primary  partition called an Extended partition and inside that extended  partition the installer will create 2 logical partitions. One for Ubuntu  and one for swap. Once we have an extended partition we (the user) can  then create a large number of logical partitions as we need.

Being limited to 4 primary partitions and having to create one Extended partition and inside it logical partitions if we wanted more than 4 partitions has been the situation since PCs first used hard disks. The issue is there whatever Linux distribution we want to install and even if we wanted to install a second copy of Windows. 

So, please be careful with your comments about the Ubuntu developers.  They do not deserve comments like that.

Regards.

---

### Post by Bucky Ball on 2016-05-13
Along with the above: If Win7 is installed in UEFI, install Ubuntu in UEFI. If legacy, Ubuntu in legacy.

Boot windows, switch off hibernation. For UEFI, boot to the BIOS and switch off secureboot (not sure if this is necessary anymore but to stay on the safe side).

At the partitioning section of the install, choose 'Something Else'. Manually partition.

Always pays to have a plan (hard copy) of what you want the outcome to look like before booting that install media.

A 2Gb /swap partition is fine unless you intend to use hibernation, in which case, same size or larger than your installed physical RAM.

---

### Post by Mark Phelps on 2016-05-13
The new hibernation option in Win8x & Win10 is known as FastStartup.  Fast Boot is a UEFI boot option, not a Windows option.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

Good Luck

---

### Post by acdcman200 on 2016-08-03
> **Mark Phelps said:**
> The new hibernation option in Win8x & Win10 is known as FastStartup.  Fast Boot is a UEFI boot option, not a Windows option.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

Good Luck

Yes I disabled that already.(both windows fast startup and uefi secure boot)

For your first thing about a 35 year old config. How would I go about update that for my hardware to the new eufi standard?

---

### Post by And6ate9 on 2016-10-19
Thank you I will try that out today.

---

