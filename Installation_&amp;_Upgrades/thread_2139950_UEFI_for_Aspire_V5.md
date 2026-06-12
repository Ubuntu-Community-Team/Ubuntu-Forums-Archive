---
title: "UEFI for Aspire V5?"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by swagatopablo on 2013-04-28
Purchased an aspire v5-571 yesterday in Singapore (my first Acer  purchase). Although it comes with windows 8 preloaded, I want to use  Ubuntu 13 as the main OS. The official ubuntu site says that for recent laptops, I  gotta install ubuntu in UEFI mode.

Can someone please tell me which is the right choice for my notebook? The legacy mode or UEFI mode? I tried the issue in Acer support forum but didn't get any definite information.

---

### Post by oldfred on 2013-04-28
If you want to easily dual boot you have to install Ubuntu in UEFI mode. Otherwise you have to go into UEFI/BIOS and change to BIOS mode to boot Ubuntu and then change to UEFI mode to boot Windows.

       You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

Several other Acer, may be similar?

 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

