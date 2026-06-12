---
title: "Dual boot Windows 7 and Ubuntu 14.04 on 2 SSDs with UEFI no GRUB2 menu"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by Albert_Chan on 2014-05-31
[FONT=arial]I currently have installed on my UEFI capable system 2 SSDs (Asus z87 motherboard). On one I have previously installed Windows 7 and on another I have just installed Ubuntu 14.04. I am trying to get them to dual boot by showing the GRUB2 menu. But so far, the system will just immediately boot into Windows or Ubuntu depending on the BIOS boot sequence. I have disabled FastBoot in BIOS already.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I've tried running Boot-repair but I keep getting "GPT detected. Please create a BIOS boot partition." I already have a separate EFI partition on the Ubuntu drive so I don't know why Boot-repair doesn't work. It's quite frustrating![/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]My paste from boot-repair can be found at: [http://paste.ubuntu.com/7560199/](http://paste.ubuntu.com/7560199/)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Any help would be greatly appreciated! I really want to get the dual boot to work. Thanks![/FONT]

---

### Post by oldfred on 2014-06-01
While system is UEFI capable, you installed Windows in BIOS/CSM mode.

UEFI and BIOS are not compatible. Once you start booting in one mode, you cannot change to the other mode. Or from grub menu you can only boot other installs installed in the same boot mode.

You installed Ubuntu in UEFI mode, so it cannot boot Windows from grub menu. You should be able to boot Windows from UEFI/BIOS or one time boot key (often f12).

Or you can use Boot-Repair to convert Ubuntu to BIOS boot. But then you have to have a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive. Use gparted to shink a partition and create the tiny bios_grub partition before using Boot-Repair to install grub to MBR.
Ubuntu boots from gpt drives with UEFI or BIOS if correct supporting partitions are on drive. Or an efi partitionfor UEFI boot or bios_grub for BIOS boot.
Windows only boots from gpt drives with UEFI.
Both Windows and Ubuntu only boot from MBR drives with BIOS.

 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

If you use Boot-Repair to convert to BIOS boot, do not install grub to all MBRs as it often suggests. Use advanced mode and select Ubuntu and sdb to install grub just to Ubuntu drive. 
You want to keep Windows boot loader on sda, so you can directly boot it when you have to repair it. Grub really only boots working Windows and getting to f8 is just about impossible from grub boot of Windows as it is too quick. 

Better still to have a Windows repairCD or flash drive.

---

