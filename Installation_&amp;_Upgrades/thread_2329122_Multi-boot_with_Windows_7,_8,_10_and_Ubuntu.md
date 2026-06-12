---
title: "Multi-boot with Windows 7, 8, 10 and Ubuntu"
date: 2016-06-28
forum: Installation &amp; Upgrades
---

### Post by jan_martin2 on 2016-06-28
Hello,

please provide insight into installing Windows 7, 8, 10 and Ubuntu 16.04 LTS.

I assume one would install in this sequence:
Windows 10, 8, 7, Ubuntu 

Ubuntu then brings Grub to stat one of the 4 OS?

200 GB / each?

Anything else to look out for?

---

### Post by X-RED_Tech on 2016-06-28
You can't install Windows 7 like the others unless you obtain an ISO file and make a USB flash with it using the Microsoft tool or Rufus. The traditional DVD media cannot install in UEFI mode.
And it's an overly complex multiboot that can break at any moment with a simple Windows update or other reasons... For what exactly? You probably don't need one Windows let alone 3...
And this is a Ubuntu forum, not a Windows forum.

---

### Post by yancek on 2016-06-28
> I assume one would install in this sequence:
Windows 10, 8, 7, Ubuntu 


Exactly backwards.  With windows you always install the most recent version last.  The UEFI problem mentioned above will complicate things.  I have the windows 10 trial version installed with windows 7 on an MBR machine so you can probably do it.   You would get better information at the microsoft site or a windows forum.  If you get the windows installed you will need to install Ubuntu in the same manner, UEFI or MBR.

---

### Post by grahammechanical on 2016-06-28
> Anything else to look out for?

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]

> 
To install Ubuntu in UEFI mode: 


[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 


[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 


[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode.    


[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 


[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 

[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The disabling of Windows fast startup also applies to Windows 10.

Regards.

---

### Post by oldfred on 2016-06-28
If older BIOS install each Windows must be in a primary partition. And you only have 4 primary partitions, so cannot let Windows use the separate boot partition.

If UEFI you may have to create multiple ESP - efi system partitions. Most systems may not work with  more than one, but you may be able to boot grub from the official ESP and chain to Windows in other efi partitions.

I might make Windows smaller and use a larger shared NTFS data partition. But with Both Windows 8 & 10 you have to  make sure fast start up or hibernation is off. If on you could not even shared between the versions of Windows.

       Dual boot two Windows UEFI from grub, two efi partitions.
[http://askubuntu.com/questions/653101/boot-repair-windows-not-listed](http://askubuntu.com/questions/653101/boot-repair-windows-not-listed)

---

