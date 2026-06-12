---
title: "\NST\AutoNeoGrub0.mbr"
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by yashachechik on 2013-11-09
Hi Guys,

I am trying to install Ubuntu 12.04.03 onto my laptop (Acer V3-571) so that I can dual boot Ubuntu and Windows 8. So far I have disabled fastboot, downloaded the boot up files onto a USB, changed from UEFI to BIOS Legacy and installed Ubuntu. I partitioned my hard drive, with 250MB for the \boot, 15Gb root partition, 75Gb home partition, 4Gb swap area and 10MB BIOS boot partition. I managed to install ubuntu successfully, however upon restart my laptop could not find any bootable device. I changed back to UEFI, went back to windows 8 and installed a dual boot program Easy BCD 2.2. When trying to dual boot Ubunutu, i get the error message "Windows failed to start.." then:
"File: \NST\AutoNeoGrub0.mbr
 Status: 0xc000007b
 Info: Application or operating system couldn't be loaded because a required file is missing or contains errors"

Any tip in the right direction would be great,

Thanks,

Yasha

---

### Post by oldfred on 2013-11-09
UEFI and BIOS are not really compatible. You cannot start to boot in one mode and then use grub or EasyBCD to switch modes.
With UEFI both systems install boot loaders in a folder in the efi partition and you boot from UEFI mode, not legacy. Only a very few UEFI systems will only boot Linux in Legacy mode only and then you have to go into UEFI and choose system to boot from that each time. You may also have to turn on or off UEFI/Legacy boot mode to match how you have installed.

You can use Boot-Repair to convert a BIOS/CSM/Legacy boot of Ubuntu into an UEFI boot.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

