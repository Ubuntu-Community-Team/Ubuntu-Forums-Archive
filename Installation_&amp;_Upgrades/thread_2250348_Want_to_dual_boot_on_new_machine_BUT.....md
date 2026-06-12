---
title: "Want to dual boot on new machine BUT...."
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by DougieFresh4U on 2014-10-28
So my computer of many years died on me. It was a triple boot machine:
UBUNTU
PINGUY
WIN7
So here I sit with a new 'box' with Win 8.1 on it and a 1TB hard drive.
The old machine I had put together, this one I bought 'remanufactured' from 
HP. No cd's/DVD's came with it.
I do not know if I can dual boot with out having to 'jump through hoops'.
When I put a DVD in, something popped up about 'wubi' which I have 
never used. I have always just booted from DVD and repartitioned and installed,
easy as it was!
How do I know if my machine will let me dual boot just as easy or do I have that 'lock' on my motherboard? I will provide what ever info if asked for.
I so much want to have my UBUNTU back!!
Thanks
Dougie

---

### Post by grahammechanical on 2014-10-28
I have never had a live session offer me Wubi and I test live sessions. Could it be that you was running Windows at the time that you put the live session disc into the drive? Wubi is no longer supported. It is no longer developed and it does not work with Windows 8.

There are several possible problems with dual booting a Windows 8 machine. It is best if you read the Wiki page as there are certain myths in circulation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. [FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[/FONT]
[/LIST]


From then on it comes down to whether you use the Install Alongside option or the Something Else option. I have heard it said many times. Defrag Windows using a Window's utility more than once, make sure Windows loads, and use Window's utilities to resize and move Windows partitions.

Better still in my opinion is to install on a second hard disk and follow the advice in the Wiki and remember the installer defaults to installing Grub into sda. It seems to be better to have Windows on one disk with its own boot loader on that disk and Ubuntu on its own disk with the Grub boot loader on that disk. Then we can use BIOS/UEFI to set which hard disk to boot from. Grub will detect a Windows install but the Windows boot loader will not detect Ubuntu.

Regards.

---

### Post by oldfred on 2014-10-28
Good advice from grahammechical.

I would only add backup of Windows and a Windows repairCd or flash drive.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


   Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

