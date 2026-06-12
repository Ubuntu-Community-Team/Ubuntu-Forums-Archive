---
title: "ubuntu 14.04.3 not recognized by windows 10"
date: 2015-12-08
forum: Installation &amp; Upgrades
---

### Post by purikyaru on 2015-12-08
hi. so, i've tried multiple solutions on these forums to fix my problems with ubuntu 14.04.3 - which share my hdd with windows 10. 
my problem is that windows 10 doesn't seem to recognize ubuntu as an operating system. it goes straight to windows on boot - but it could recognize a program like unetbootin before. ubuntu ***is ***successfully installed on my laptop - it is residing in a 200gb partition with about 5gb of swap area. windows 10 is allocating about 600gb on my other partition, and i'm saving 50gb or so for a future mac os x or linux distro. 

i have a dell inspiron 15 i5558 with 1tb hdd. primarily runs windows 10, hoping to tri-boot mac os x (yosemite or el capitan), win10, and ubuntu 14. i need to be able to do this for my school's robotics program (i'm on the programming/CAD team), and we are using windows and linux for programming, mac os x so it is compatible with ipads/airplay. 

if it helps, ubuntu also didn't recognize win10 during the installation process, which is why i had to manually set up my partitions (which, honestly, was no hassle). 
but, here is what i have tried to do so far to get this to work:

1) reinstalling multiple times. the first time, it said i installed ubuntu on legacy boot. so, i reinstalled that onto uefi boot, but windows doesn't recognize it still. the installations were successful each time with no errors, and updates were downloaded during the installations. i installed from a boot disk (i don't have a usb), and i had difficulties with the wubi.exe installer before, but windows recognized it then but would not launch it.
2) boot repair via linux terminal. i started up from disk, and then selected the "try linux" option. i ran boot repair, but it failed and would not fix the recommended method because i run from uefi boot. that is when i reinstalled ubuntu after i remembered i installed it on legacy boot. still did not work.
3) windows control panel > boot manager. i tried seeing if windows recognized ubuntu as an operating system also residing within my laptop, and it did not. 
4) creating/deleting/formatting partitions. i reformatted the partitions ubuntu was previously installed on, and deleted unnecessary partitions, while creating a new one for the swap area. windows recognizes the partitions as allocated, but does not recognize ubuntu on them.

any suggestions would be greatly appreciated - at this point, i will be willing to try anything. thank you very much! (:

---

### Post by westie457 on 2015-12-08
Welcome to UF purikyaru.

That is a lot of issues.
Some things you have tried to install Ubuntu will never work with Windows and UEFI booting, using Wubi is one of them.

Give us a clue on how your system is at the moment. Run Boot Repair again, do not select any options for repair just select the option to create a Boot Info report. Post the generated link here so we can check what the current issues are.

Thank you.

---

### Post by grahammechanical on 2015-12-08
Microsoft does not believe that Windows users should use any other operating system. So, forget about Windows not recognising Ubuntu. Windows boot loaders are never going to recognise the existence of anything but a Microsoft OS.

On the other hand, the Linux boot loader Grub will recognise Windows boot loaders and it is Grub that a standard Ubuntu installation process should install in the Master Boot Record (MBR) of the hard disk unless we tell the installer to do something different. But we have to follow the guidance in this wiki page.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

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
[*]Then:
[LIST]
[*]nothing  special is required if you use the automatic installer of Ubuntu  ("Install Ubuntu alongside others" or "Erase the disk and install  Ubuntu"). Important: if you have a pre-installed Windows and you want to  keep it, do not choose "Erase the disk and install Ubuntu". 
[*]if  you use the manual partitioning ("Something else"), the difference is  that you will have to set the /boot/efi mount point to the UEFI  partition. And if there was not any UEFI partition on your HDD, you  first will have to create it 
[/LIST]
   
[/LIST]


Oh, Boot Repair gives us a URL to a location where its report is stored. Posting that URL in the thread is always useful even though none of us here have had any special training to understand all it says. But sometimes we do get a clue from the Boot Repair report.

Regards.

---

### Post by kurt18947 on 2015-12-08
I have no idea about hardware support but how about running two of the 3 O.S.s in virtual machines? I've never tried OSx in a VM. Virtualbox does list OSx as a possible guest so presumably it works.

---

### Post by Bucky Ball on 2015-12-08
Welcome. Just to reiterate one point: if you want to share data between Windows and Ubuntu use a shared NTFS partition. Windows won't recognise EXT partitions, no.

Also, you have a much better chance of support if you post one support request per thread (one problem) in future. :)

Good luck.

---

### Post by yancek on 2015-12-08
As pointed out above, WUBI will not work on windows 8 or newer and is also no longer being developed or supported.  See the WUBIGUIDE at the site below.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you have windows installed UEFI, you must install Ubuntu UEFI.  Explained at the Ubuntu link below.  If you are using GPT, you must have windows UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You can share data partitions between Linux and windows but you need to use vfat or ntfs as windows doesn't recognize much less read or write to a Linux partition.  Not that they couldn't do it obviously, it's a simple business decision.  No money in it for microsoft.

---

