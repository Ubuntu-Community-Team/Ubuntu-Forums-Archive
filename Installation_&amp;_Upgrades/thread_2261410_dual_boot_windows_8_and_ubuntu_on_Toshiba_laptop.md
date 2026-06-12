---
title: "dual boot windows 8 and ubuntu on Toshiba laptop"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by urso2 on 2015-01-18
I reviewed the thread "how to dual boot Ubuntu 10.10, windows 7 on Toshiba laptop'
My question is related but not the same, as I have not been able to initially install Ubuntu.


It appears my laptop does not recognize a bootable USB formatted for non-EUFI.
If anyone has worked through this issue please advise me on how to proceed.
Below are the steps I have tried to get this working.


I am trying to install ubuntu 14.04 (desktop - ubuntu-gnome-14-10-desktop-amd64.iso) to dual boot on my Toshiba laptop (Satellite C55D-A5304 bios version 1.80).

I used "universal USB Installer v1.9.5.9' to create a bootable flash drive from the iso.
I configured the following settings on my laptop bios:
Secure Boot       [Disabled]
Boot Mode         [CSM Boot]
Boot
                1. USB
                2. ODD
                3. HDD/SDD
                4. LAN
 
I inserted the USB and attempted to start the laptop and received the following message:
Missing operating system.
 
Intel UNDI, PXE-2.1 (build 083)
Copyright (C) 1997-2000 Intel Corporation
This Product is covered by one or more of the following patents:
US5, 307,459, US5,434,8723 US5,732,094, US6,570,884, US6,115,776 and US6,327,625
Realtek PCIe FE Family Controller Series v1.31 (03/15/13)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
No bootable device -- insert boot disk and press any key
 
I removed the Ubuntu USB and attempted to boot - received the same message.
 
I restarted the laptop and changed the following bios settings and removed the USB

Boot Mode         [UEFI Boot]
(all other bios settings remained as above)
 
The laptop booted normally into the windows 8.1 operating system.
 
I re-inserted the Ubuntu USB and shutdown the laptop, and started it again
The laptop again booted normally into the windows 8.1 operating system
 
I removed the Ubuntu USB and inserted my Windows Recovery USB.
I shutdown the laptop, and started it again
The laptop again booted normally into the windows 8.1 operating system

I shutdown the laptop and made the following changes to the bios.
Secure Boot       [Enabled]

The laptop booted to the Recovery Options to choose your keyboard layout 
 
I shutdown the laptop, removed the Windows Recover USB and re-started it.
The laptop booted normally into the windows 8.1 operating system.

---

### Post by sudodus on 2015-01-19
I have a fairly new Toshiba where Ubuntu works in UEFI as well as in BIOS mode, maybe not too different from yours. See some experiments described in these links.

                          [One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682")                 

                           [Portable installed system that boots in UEFI as well as in BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631")                 


> **urso2 said:**
> ...
I am trying to install ubuntu 14.04 (desktop - ubuntu-gnome-14-10-desktop-amd64.iso) to dual boot on my Toshiba laptop (Satellite C55D-A5304 bios version 1.80).

Are you trying 14.04.1 LTS or 14.10, or both?
> 
I used "universal USB Installer v1.9.5.9' to create a bootable flash drive from the iso.
I configured the following settings on my laptop bios:
Secure Boot       [Disabled]
Boot Mode         [CSM Boot]
Boot
                1. USB
                2. ODD
                3. HDD/SDD
                4. LAN
 
I inserted the USB and attempted to start the laptop and received the following message:
Missing operating system.
 
Intel UNDI, PXE-2.1 (build 083)
Copyright (C) 1997-2000 Intel Corporation
This Product is covered by one or more of the following patents:
US5, 307,459, US5,434,8723 US5,732,094, US6,570,884, US6,115,776 and US6,327,625
Realtek PCIe FE Family Controller Series v1.31 (03/15/13)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
No bootable device -- insert boot disk and press any key
 ...

Your computer does not boot from the USB pendrive.

-o-

- Have you switched off fast boot - and in general switched off all Windows hibernation and semi-hiberation?

- Are you working in linux or Windows, when creating the pendrive?

-o-

There are different tools ...

- Please check with ***md5sum***, that the downloaded iso file is good (md5summer in Windows). See this link

 [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Try another tool to make the pendrive bootable (not universal USB Installer) according to this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

***mkusb*** and ***Win32 Disk Imager*** work in most situations, and I recommend them particularly if you want to install 14.10. Otherwise you can expect good results also with the ***Unetbootin***.

I press ***F12*** right at boot/reboot and get a menu of boot alternatives as well as the alternative to edit the UEFI menus. Try that! Sometimes it is important to shut down completely (reboot is not always enough to clear the computer from what was running before reboot).

---

### Post by Gordonbp531 on 2015-01-19
if you are dual-booting with Windows 8, then don't touch any setting in the BIOS. (There's no need to turn UEFI off, or secure boot, or Fast boot if you have it)
This is how to do it:
1. Create free space on HDD in windows. If you do this with GParted, then there is a good possibility the Windows installation will be borked.
2. Boot from live CD/DVD/USB
3. Choose "Something else" when asked if you want to install on the whole disk...
4. Create two partitions for / and Home plus a swap area in the free space.
5. Install
4. make sure that GRUB is installed on the EFI partition. (Computers with pre-installed Windows 8 have a EFI partition already)
5. If Grub doesn't show up when you re-boot, you may have to add the entry as  an aprroved boot key in the BIOS

It's as easy as that....

PS - I've done this successfully on two totally different makes of computer with Windows 8 pre-installed...

---

