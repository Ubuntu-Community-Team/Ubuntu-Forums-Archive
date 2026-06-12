---
title: "EFI Dual Boot Help"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by luishasbon on 2012-02-06
Hi Im trying to install ubuntu in a gpt system with windows 7, The ubuntu installation process goes ok, I install the grub in sda1 the windows loader partition, after reboot, it goes directly to windows, doesnt show up the grub menu. How is supposed this kind of installation to be done?? Thanks!

---

### Post by oldfred on 2012-02-09
If you are installing to gpt with Windows you must be using UEFI. Then the first partition must be /efi not a Windows boot. The second partition is then the Windows boot.

Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
Post #76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
efi\Microsoft\Boot\bootmgfw.efi

There are/were some bugs where Ubuntu overwrote the efi partition, so before installing you need to backup efi partition.

Older Windows info on gpt - 2008
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

---

