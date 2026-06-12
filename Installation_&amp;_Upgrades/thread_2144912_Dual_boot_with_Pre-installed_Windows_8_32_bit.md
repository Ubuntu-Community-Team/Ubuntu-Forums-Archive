---
title: "Dual boot with Pre-installed Windows 8 32 bit"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by zoezo on 2013-05-13
Hi, all. I'm having some problems with dual booting Windows 8 and Ubuntu. Ubuntu boots fine now that I'm running legacy BIOS and disabled secure boot, but now there's no option to select Windows 8. In addition, I can't use boot repair because it's incompatible with my 32 bit version. Is there a way around this?

---

### Post by oldfred on 2013-05-13
If you have Windows 8 pre-installed, it boots with UEFI from gpt partitioned drive.
But if you installed 32 bit (why?) then you cannot easily dual boot. You have to go into UEFI/BIOS and turn off secure boot and UEFI and turn on CSM or BIOS to boot Ubuntu. Then to boot Windows you have to turn off CSM and turn on UEFI and secure boot.

Only Ubuntu 64 bit has UEFI support. And BIOS or UEFI write system info differently for systems to use so you cannot dual boot from grub or any other system.

         
You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 
One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

---

