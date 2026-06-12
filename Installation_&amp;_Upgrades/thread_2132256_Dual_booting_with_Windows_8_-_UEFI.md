---
title: "Dual booting with Windows 8 - UEFI"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2013-04-04
Hi - been an Ubuntu user since version 7!
Got a new Lenovo U410 notebook (lovely!) that has this other new OS on it.
As it's in warranty for 10 months still, I want to dual-boot with Ubuntu without damaging the other OS install or boot. I expect that when the warranty runs out I shall remove Windows 8 completely...

I know that 12.10 will boot in EFI mode as I've done it from a flash drive.
Should I wait for 13.04? Will that make things easier?

What I'm really looking for is some assurance (and tips on how to do it) that when I do the dual boot, it won't wreck the Tiles install!
I have to say I'm a bit nervous about this as the machine comes with only a Recovery partition. I have made a System Image backup...

Any help would be appreciated...

---

### Post by oldfred on 2013-04-04
Another thread on same issue. Intel SRT makes it more complicated to install and now with UEFI and secure boot it is not exactly easy.

[http://ubuntuforums.org/showthread.php?t=2122351](http://ubuntuforums.org/showthread.php?t=2122351)

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

