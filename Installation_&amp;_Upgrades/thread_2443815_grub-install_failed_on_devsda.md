---
title: "grub-install failed on /dev/sda"
date: 2020-05-20
forum: Installation &amp; Upgrades
---

### Post by maxence1223 on 2020-05-20
Hello everybody,
I'm new on ubuntu, and i download ubuntu on a usb boot, for boot on my live usb. Before that I was on windows 10. The problem comes when I choose install ubuntu on the internal hard drive. The message "Running grub-install on /dev/sda failed. Fatal error".
I want to install ubuntu 20.04 on my hard drive, and I try some solutions as erase the entire disk to let ubuntu make its own partition table, use boot-repair to resolve the problem, but all this solutions failed, and the same message comes : "Running grub-install on /dev/sda failed. Fatal error".
Someone can help me ???
Thanks

---

### Post by oldfred on 2020-05-20
Post link to Summary Report from Boot-Repair.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by maxence1223 on 2020-05-20
I do that as you said :
[HTML]https://paste.ubuntu.com/p/YCz4m4tJ8k/[/HTML]

---

### Post by oldfred on 2020-05-20
Do you have system set to boot in UEFI boot mode.
It looks like you have a bootable UEFI install.
But I might turn off UEFI Secure Boot.

It looks like you created a bios_grub partition. But that has to be unformatted, not FAT32. And only needs to be 1MB.
It also is only for BIOS boot of grub on gpt drives, and you have UEFI boot, so bios_grub not needed.
Also you cannot boot in BIOS mode with UEFI Secure Boot on.
You can delete that partition if desired.

---

### Post by maxence1223 on 2020-05-20
I'm new so I don't understand very well what u said,
1) I think I have a system boot on UEFI, because I can turn on my computer and boot via the boot menu on my usb.  
2) Yes I create this partition bios_grub, but I can erase it, it don't need.
3) How can I turn off UEFI secure boot ? (edit I search the web and find a way to do that, but I can't because I don't know the password of the boot, so I can't configure it ...) If you know a way to solve this problem ...
4) Turn off the UEFI secure boot can help me to install Ubuntu on my hard drive ? Because now, my Ubuntu is on my usb, and I use Ubuntu on it, and I want to install it on the hard drive of my compunter.

Thanks to your help :)

---

### Post by grahammechanical on 2020-05-20
Here are a couple of Ubuntu community help documents that might help. Ubuntu has been compatible with secure boot for many years because the Ubuntu developers went so far as getting the boot loader and the Linux kernel certified to be compatible with the Microsoft secure boot protocol.

[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)


Here is how to install Ubuntu on a hard drive in a UEFI motherboard.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Notice these general principles

> To install Ubuntu in UEFI mode: 

[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 

[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 

[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode.    

[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 

[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 

[*]Then: 
[LIST]
[*]nothing  special is required if you use the automatic installer of Ubuntu  ("Install Ubuntu alongside others" or "Erase the disk and install  Ubuntu"). Important: if you have a pre-installed Windows and you want to  keep it, do not choose "Erase the disk and install Ubuntu". 
[*]if  you use the manual partitioning ("Something else"), the difference is  that you will have to set the /boot/efi mount point to the UEFI  partition. And if there was not any UEFI partition on your HDD, you  first will have to create it (see the "[Creating an UEFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_UEFI_partition")" paragraph below). 

[/LIST]
[/LIST]
[IMG]http://pix.toile-libre.org/upload/original/1347270713.png[/IMG]

Regards.

---

### Post by oldfred on 2020-05-20
You show Ubuntu installed on sda your 120GB drive in UEFI boot mode.
But boot live installer on 4GB flash drive.

You have to know UEFI password for most systems to make any changes.
Many systems call UEFI Secure Boot as "Windows" or "Other". 
They often had fine print in manual saying if you are booting Windows 7 you have to use Other. Windows 7 did not support UEFI Secure Boot.

---

### Post by maxence1223 on 2020-05-21
Ok I understand, 
But I lost my BIOS password, how can I resolve it ?
Thanks

---

### Post by yancek on 2020-05-21
I see you have/had Linpus Linux installed so that means you have an Acer.  Is the password you refer to the Supervisor password for the BIOS?  If so, you will likely need to do an online search on how to change this password on an Acer. Some info on that at the link below which might help.

 [https://www.ifixit.com/Answers/View/110108/How+can+I+reset+bios+password](https://www.ifixit.com/Answers/View/110108/How+can+I+reset+bios+password)

---

### Post by maxence1223 on 2020-05-21
My computer is an HP probook x360 g1 ee 11.
I see on the web that for reset the BIOS, and the password, we can put off the battery of the CMOS on the computer. So I do that, I turn off this battery for some seconds, and the computer message me that the CMOS is invalid, and that he need to reset the BIOS, that cool ! But then the BIOS was reset, the password is a always here. So I put off the battery for 30 minutes, but it failed, because the password is always here. 
If anybody can help me please ? ;)
Thanks

---

