---
title: "Cannot install (or launch) Ubuntu MATE 15.10 on laptop"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by Will_Cassella on 2015-10-24
Hi,

I'm trying to install Ubuntu MATE 15.10 alongside Windows 10 on my laptop. I downloaded the ISO from the Ubuntu MATE website, and after checking the MD5 sum I made a bootable USB drive using PenDriveLinux. I restarted my computer, and booted from the USB drive.

I was greeted with a loud BEEP from my computer, and a screen showing "Try without installing..." "Install..." etc. I chose "Install" and the Ubuntu MATE logo appeared with several dots below. The dots changed color for a few seconds until they stopped completely, and the computer became unresponsive. After letting it sit for quite some time I force-restarted the computer. Selecting "Try without installing" produced the same result.

After returning to Windows and doing a bit of googling to no avail, I rebooted and choose the "Check disk integrity" option from the USB menu. After running for a bit, it said I had two invalid files.

After that I tried re-formatting the USB drive using Rufus instead of PenDriveLinux. Now, booting to the USB skipped the menu and beep entirely, and brought me straight to the Ubuntu MATE logo. I found that pressing the up arrow on the keyboard would let me view logs of the process. It said something about not being able to change the password, and to "repeat this process for all CDs in set". It seemed to make progress for a bit, then it said "pci_pm_runtime_suspend() returned -16" and began giving me messages about cpu stalls. After this point, it did not seem to be making any progress and I restarted it.

After that, I tried burning the image to a DVD and booting from that. I got the same result as last time, only it began spouting call stacks in the log.

Beyond that I have not had any luck. Using the same image to install on a virtual machine on Windows worked perfectly fine, so I don't think it's a software issue.

I'd really like to get this installed this weekend, but at this point I just don't know what to do. I'd appreciate any help you guys can give me.

---

### Post by kansasnoob on 2015-10-25
I don't have any ideas or answers but I'll give you a bump so maybe someone else will have an idea.

---

### Post by grahammechanical on 2015-10-25
So, what do we know? Ubuntu Mate runs fine in a VM but the Ubuntu Mate live session does not get very far when running on the actual hardware. Would you agree? Is this the 64bit version of Ubuntu Mate or the 32bit version? Are you loading the ISO image in EFI mode? You may need to use one or more of the F6 options to set different boot parameters.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Pre-installed Windows 10 comes with secure boot on and installed in EFI mode. So, this applies

> if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too.

And this

> 
[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. 
[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 
[/LIST]


The ISO image should be the AMD64 image and not the i386 image.

To change boot parameters of the live session go down to the heading Changing the CD's Default boot options section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards

---

### Post by Geoffrey_Arndt on 2015-10-25
Couple thoughts . . . it may be smart to delete the mate partition via gparted live CD (may have broken remnants from 1st install attempt).   Also, if you had Windows 10 "hibernation" start up during the install process, that will hose the install process.   Might want to check your uefi firmware setup or win power settings to ensure hibernation is disabled before attempting another install.

---

### Post by Bucky Ball on 2015-10-26
When you get to the 'Try Ubuntu' 'Install Ubuntu' etc screen, hit F6 and choose 'nomodeset'. Proceed to 'Try Ubuntu'. Any different?

---

