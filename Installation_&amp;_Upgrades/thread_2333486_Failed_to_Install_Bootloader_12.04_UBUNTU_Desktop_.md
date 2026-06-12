---
title: "Failed to Install Bootloader: 12.04 UBUNTU Desktop 32-bit on SSD that came with Win10"
date: 2016-08-10
forum: Installation &amp; Upgrades
---

### Post by wilsoie on 2016-08-10
I have a new desktop PC that came with Windows 10 64-bit version installed on it. I do not need the Windows OS but I am trying to Install Ubuntu Desktop version 12.04 32-bit version which I must have to support a specific software program for my company.  The problem I am having is the installation "Fails to Install Boot Loader" no matter how I partition the drive. (so far) Ubuntu version 14.04 32-bit installs correctly and works fine. Unfortunately, the program we are running is  NOT supported yet in the newer Ubuntu versions. 

I tried many of the other troubleshooting blogs/steps and so far nothing has worked. I did run the Boot-Repair and here is the output: [http://paste.ubuntu.com/22877456/](http://paste.ubuntu.com/22877456/)

I suspect the issues has something to do with the Windows 10 installation being in UEFI boot and the 32-bit 12.04 UBUNTU does not support EFI boot. 
I tried messing around with the UEFI mode versus Legacy boot mode, but when I switch it, then my SSD doesn't show up at all in the Ubuntu Installation Partitioning menu...
I've cleared all the partitions on the SSD and windows is gone, but is there another step I need to take in order to wipe the boot mode or MBR? from the SSD prior to installing UBUNTU?
By the way, I'm using USB 12.04 LIVE made with UNETBOOTIN for installation...   Also, the 12.04 doesn't come with support for my Ethernet card so I have to install the new E1000E drivers first before the internet connection works...    If someone has the steps I should take to make sure my SSD is wiped clean from the UEFI boot mode that came with the WINDOWS 10 install, reformat, repartition, and install UBUNTU 12.04 32 bit WITHOUT getting that "Failed to Install Bootloader" error, I would be VERY much grateful to that person!!  Thank you.

---

### Post by oldfred on 2016-08-10
I think you are asking a lot for 4 year old software to work on a new UEFI system.
Drivers & kernel have changed a lot to allow new hardware to work.

Summary report says UEFI Secure Boot may be on. You will have to have that off. CSM does not work with Secure boot on.
And you just about have to install & boot in CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

But report is only showing DVD & two flash drives, no hard drive at all?
It should at least show drive, unless new NMVe drive.

If system was Windows 10, then drive was partitioned as gpt, not the 35 year old MBR(msdos). I have used gpt since about Ubuntu 10.10 on one drive when I still had XP on a MBR drive booting in BIOS mode. 
But gpt requires a 1 or 2MB unformatted partition anywhere on drive for grub to install correctly for BIOS boot. With UEFI, you have an ESP - efi system partition for UEFI boot. Since UEFI came out, I changed to just the bios_grub partition to both the ESP & bios_grub for all new drives including some larger flash drives.

What SSD? I think it was about 12.04 that I first used a 60GB  SSD on my old BIOS based system. I did have to turn on AHCI which prevented XP from booting, so I shut XP down.

It may actually be easier to convert software to 64 bit & work with 16.04.

---

