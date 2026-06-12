---
title: "Can't boot Ubuntu after installing it on laptop with Windows 10"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by david523 on 2016-06-02
Hey guys, I'm new to dual booting, and I've installed Ubuntu 16.04 on my computer. No matter what, when I turn my computer on it defaults to Windows 10 and gives no option to boot to ubuntu. I have a sony vaio laptop that came with Windows 8, but I upgraded to Windows 10 when it came out.

A couple things first:
My computer has a UEFI boot loader
Secure boot and fast boot are disabled
The hard disk is first in boot priority
The installation was successful (though in some tutorials I've seen, they have the ability to keep using ubuntu after installing, mine requires a restart)
Windows does not recognize that Ubuntu is installed when I go to choose a default operating system (and I set it to give 30 seconds to choose an OS)
I installed ubunutu alongside Windows and did not manually create anything other than the free space to use.

As I said, I'm pretty new to this, so I don't know what all I need to provide so let me know if I need to give more. I can't boot into Ubuntu in any form except from the USB to either try it, or install it, which I've already done. Any help is appreciated!

---

### Post by yancek on 2016-06-02
Read the Ubuntu documentation at the link below and compare the recommendations to what you did during the install.  First off, if windows is UEFI then you must boot and install Ubuntu UEFI.  The behavior you are experiencing is expected if you did not install Ubuntu UEFI but it could be something else.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Part of the problem may be that you have a Sony which as I understand, does not comply with UEFI standards.  

You can continue using Ubuntu after the install from the DVD or flash drive but that is only running it as a Live CD and no changes of any kind will be saved.  You need to reboot to the installed system.

A default windows install will not recognize a Linux partition/filesystem other than to show it as a partition in Disk Management.  You cannot read it or write to it from windows without getting some third party software.

Did you use the "Install Alongside" option?  That might be part of the problem if you are using UEFI as it is best to use  the manual method which is called "Something Else" in Ubuntu.

If you are unable to resolve the problem, go to the site below using the Ubuntu DVD and get the boot repair software and run it.  Select the option to Create BootInfo Summary and do not try to make any repairs.  Post a link to the output here and someone should be able to help.

---

### Post by grahammechanical on 2016-06-02
> though in some tutorials I've seen, they have the ability to keep using ubuntu after installing, mine requires a restart)

When we load the Ubuntu installer we will get an option to Try Ubuntu Or Install Ubuntu. If we select Install Ubuntu then after the installation process is finished the only option is to restart - remove install media & press Enter.

If we select Try Ubuntu we load to a desktop environment. There will be an Install Ubuntu icon on the desktop. If we click that icon and install Ubuntu then at the end of the process we will get an option to restart or continue testing. 

> Windows does not recognize that Ubuntu is installed when I go to choose a  default operating system (and I set it to give 30 seconds to choose an  OS)

Where are you going to make the choice of which OS should be the default OS? Somewhere in Windows? Or in the UEFI setting utility?

Regards.

---

### Post by oldfred on 2016-06-02
It is my understanding that Sony (and others) violate UEFI standard and use description as part of boot. And of course the only valid description is "Windows Boot Manager". 
But there are work arounds. If dual booting UEFI has a fallback or hard drive boot entry which is the same for external drives. That is /EFI/Boot/bootx64.efi.
If we copy shimx64.efi into /EFI/Boot and rename to bootx64.efi, you then should be able to boot a hard drive entry. Or may have to create a hard drive entry that will work. The ubuntu entry will not.

       Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589) 

[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

