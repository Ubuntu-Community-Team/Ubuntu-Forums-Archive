---
title: "A black screen is displayed instead of my grub menu"
date: 2014-12-18
forum: Installation &amp; Upgrades
---

### Post by darkmatter3 on 2014-12-18
I reinstalled ubuntu 14.04 over my old one using a bootable pendrive, and deleted the windows files, now it shows me a black screen whenever I start, however it automatically redirects to ubuntu. And, I'm now unable to install windows using again a bootable pendrive and just redirects to ubuntu.
My boot repair gave the following link
[http://paste.ubuntu.com/9560890/](http://paste.ubuntu.com/9560890/)

---

### Post by oldfred on 2014-12-18
Your drive is gpt partitioned.
Ubuntu will boot from gpt partitioned drive with either UEFI or BIOS boot if correct partitions are on drive for each type of boot. 
You have both the efi partition for UEFI boot, and grub installed to both the protective MBR and the partition boot sector of sda2. You almost never install grub to a partition and with gpt grub will not install correctly to MBR for BIOS boot unless you also have the bios_grub partition which is the error Boot-Repair gave. It seems you booted Boot-Repair in BIOS mode. Better to always use UEFI.

You may be trying to boot in BIOS mode and then system switches to UEFI and that is why you have the boot issues. You should have secure boot off, UEFI on or CSM/BIOS off.

How you boot install media, is how it installs. So you always want to boot flash drive or DVD in UEFI mode.

Windows will only install in UEFI mode on a gpt partitioned drive. And if you force a BIOS install it will convert drive to MBR and in effect erase Ubuntu and all the gpt partitions.

You can convert a Windows 7 installer from BIOS to UEFI, Windows 8 should be configured to boot either way.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

    
Windows does not see Linux partitions, so it has no place to install to. You need to shrink sda2 to make unallocated space for Windows. If you create partitions for Windows in advance know it has extra requirements for UEFI type installs and order of partitions on drive is important.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

