---
title: "No EFI System Partition was found"
date: 2020-02-12
forum: Installation &amp; Upgrades
---

### Post by maxutil on 2020-02-12
Attached are screenshots of what I'm seeing when attempting to install Ubuntu on a PC with Windows 10 already on it. I made a separate partition of 100 GB (as seen in the screenshots) intending to install Ubuntu on it.

I googled my problem and saw a reply here: [https://askubuntu.com/questions/1144552/dual-boot-no-efi-system-partition-was-found](https://askubuntu.com/questions/1144552/dual-boot-no-efi-system-partition-was-found)

So based on that, do I need to create two partitions when I'm in Windows? One partition should be smaller and this just holds the Linux OS and apps, and a separate partition will hold other data that I intend to create/store? I wanted to reserve 100 GB or so for all Linux-based data. How many partitions, what sizes, and what settings do I need to set on those partitions?

I also want to be able to access files in both Windows and Ubuntu if that makes a difference. Any advice here would be appreciated.

Below is the 100GB partition I made while in Windows to dedicate to Linux.
[IMG]https://imgur.com/1TBm8oF[/IMG][ATTACH=CONFIG]285005[/ATTACH]

I chose these settings and Mount Point \
[ATTACH=CONFIG]285006[/ATTACH]

This message comes up
[ATTACH=CONFIG]285007[/ATTACH]

---

### Post by CatKiller on 2020-02-12
So, the error is exactly what it says: you're trying to install Ubuntu in UEFI mode without the necessary EFI System Partition.

Since you're trying to install alongside Windows 10, and your Windows 10 is *not* in UEFI mode (otherwise you'd already have an ESP) you don't want to install Ubuntu in UEFI mode, either. The mode that Ubuntu installs in is determined by the way that you boot the installation media: one way is UEFI mode (which would probably be part of the label when you're choosing it from the boot menu) and the other way is the (much) older BIOS mode. Boot your installation media in BIOS mode, and it will install Ubuntu in BIOS mode. Then it won't need (or use) an ESP: Grub (the Linux bootloader) will be installed into the Master Boot Record of your drive, and will then chainload the Windows bootloader. In UEFI mode both the Linux bootloader and the Windows bootloader would be in the ESP.

Since OEM installs of Windows 10 are done in UEFI mode, I guess the Windows install was one that you did yourself.

---

### Post by maxutil on 2020-02-12
> **CatKiller said:**
> So, the error is exactly what it says: you're trying to install Ubuntu in UEFI mode without the necessary EFI System Partition.

Since you're trying to install alongside Windows 10, and your Windows 10 is *not* in UEFI mode (otherwise you'd already have an ESP) you don't want to install Ubuntu in UEFI mode, either. The mode that Ubuntu installs in is determined by the way that you boot the installation media: one way is UEFI mode (which would probably be part of the label when you're choosing it from the boot menu) and the other way is the (much) older BIOS mode. Boot your installation media in BIOS mode, and it will install Ubuntu in BIOS mode. Then it won't need (or use) an ESP: Grub (the Linux bootloader) will be installed into the Master Boot Record of your drive, and will then chainload the Windows bootloader. In UEFI mode both the Linux bootloader and the Windows bootloader would be in the ESP.

Since OEM installs of Windows 10 are done in UEFI mode, I guess the Windows install was one that you did yourself.

Hi I was able to install Ubuntu from the time that I originally posted. When I boot the system, there are actually 2 ways to boot through USB. One is through legacy and one through UEFI. Before I was choosing UEFI, but this time I chose Legacy. I followed the prompts, and was still unsure what partition Ubuntu was going to get installed to, but I just went with it. And in the end, the installation process chose the 100GB empty partition as the partition to install to. And from here I can access my files from my other partition. So thank you for the reply.

I'm brand new to Linux and learning how to use this thing

---

### Post by EuclideanCoffee on 2020-02-13
Welcome to Ubuntu and Linux in general. EFI is required for UEFI as you're now well-aware. EFI is a special partition that boots the Linux system. Linux and Windows can use multiple partitions if their systems are set to "mount" them.

At the time of installation, you want an empty partition. The installer is smart enough to know when a partition is empty, and generally, you can have a running system working with just allowing the installer to find the partition. Sometimes people may say that they make their own partitions, but making your own partition largely depends on special knowledge of how they work together to create a system. The community has provided enough knowledge and software to allow you to not need to know much to get a working system up and running, fortunately.

So glad you were able to get a Legacy configuration running. In the future, if you want to switch to UEFI, you should be sure to boot into UEFI and then allow the installer to create the boot configuration. If it's having trouble, it's likely due to whatever Windows has done with its partitions. You may want to consider deleting a recovery partition. But that is up to you. Good luck and enjoy learning more about Linux. :D

---

### Post by dave_in_roanoke on 2020-09-22
Maxutil I have the same problem ( "No EFI System Partition was found. This system will likely no be able to boot...continue at you own risk" ) . 


Was your selection "2 ways to boot through USB. One is through legacy and one through UEFI" made when you created the USB(?) or during install(?)


What did you use to "burn" the USB?


Thanks

---

### Post by CelticWarrior on 2020-09-22
@dave_in_roanoke

Please do not revive old threads, open your own if you must. You don't, if you care to read this one and understand UEFI vs BIOS boot processes and consequently how to boot and install in one or the other.

Also guidance was provided a year ago - [https://ubuntuforums.org/showthread.php?t=2427664](https://ubuntuforums.org/showthread.php?t=2427664) - but no feedback from you.

---

