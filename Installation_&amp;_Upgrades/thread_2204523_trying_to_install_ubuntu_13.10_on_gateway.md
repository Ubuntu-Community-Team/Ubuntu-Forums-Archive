---
title: "trying to install ubuntu 13.10 on gateway"
date: 2014-02-08
forum: Installation &amp; Upgrades
---

### Post by iamrandy on 2014-02-08
i am trying to install ubuntu 13.10 on a gateway with windows 8 on it and the windows boot manager tells me that windows has failed to start and it gives me the file i think its trying to say is at fault it is \ubuntu\winboot\wubildr.mbr. Does anyone have any suggestions. Any would be helpful. Thank You

---

### Post by bc.haynes on 2014-02-09
Were you trying to use wubi to install 13.10 on the same drive?

---

### Post by bc.haynes on 2014-02-09
From the [[color=blue] Wubi Megathread:[/color]](http://ubuntuforums.org/showthread.php?t=1639198)

> Wubi, which stands for Windows-based Ubuntu Installer, is a convenient and easy way to try another operating system without the hassle of partitioning or other issues that sometimes occur when attempting to run more than one operating system.
Wikipedia

Wubi uses a virtual disk mounted within the host system (Windows), allowing users to access the full functionality of Ubuntu after the computer starts and the operating system has been chosen from the available menu.
Wubi Guide

However, Wubi was never intended as anything other than a means to try a Linux operating system and, as such, it is usually recommended to install Ubuntu to a dedicated partition on the hard-drive.

See **Problem #2 **in the Wubi Megathread.

---

### Post by iamrandy on 2014-02-09
well yes that is essentially what i was trying to do so where am i going wrong

---

### Post by bc.haynes on 2014-02-09
Can't do that.

You need to install from a [[color=blue]Live CD/DVD [/color]](https://help.ubuntu.com/community/BurningIsoHowto) or a bootable [[color=blue] LiveUSB[/color]](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows), and not from the same drive you are running Windows on.

---

### Post by oldfred on 2014-02-09
If you have pre-installed Windows 8, it uses UEFI with gpt partitioning. And wubi does not work with gpt partitioning.

Also the last supported version of wubi is 12.04 for above reason, as all new computers are UEFI.

 Wubi for Windows 8 UEFI, not really recommended
[http://ubuntuforums.org/showthread.php?t=2196044](http://ubuntuforums.org/showthread.php?t=2196044)

---

### Post by iamrandy on 2014-02-09
i've tried doing the whole bootloader thing and got to actually get the ubuntu loading screen up and it went no where from there i'm downloading and installing a new disk from another computer i think my burn was at fault

---

### Post by iamrandy on 2014-02-09
so i've burned the new disk was able to boot on the disk but it is now telling me that the is not another os detected and wants to delete the whole disk to install ubuntu. Is there any way to partition windows and ubuntu

---

### Post by oldfred on 2014-02-09
Did you turn off fast boot or always on hibernation. The installer cannot see Windows if hibernated.
Or it could an Ultraboot with Intel SRT?
See links in my signature including:

 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by iamrandy on 2014-02-10
sorry i said screw it and just deleted windows 8 and installed ubuntu.  Windows 8 is horrible anyway. But as usual when i needed some help i got exactly what i needed. 

                                                       I LOVE UBUNTU

---

