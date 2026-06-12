---
title: "Should I install Ubuntu in MBR partion?"
date: 2020-09-29
forum: Installation &amp; Upgrades
---

### Post by EngineerStrange on 2020-09-29
Actually I need to install windows but it doesn't support gpt partition so that's the problem.

---

### Post by oldfred on 2020-09-29
Depends on your hardware.
Microsoft has required vendors to install Windows in UEFI boot mode on gpt partitioned drives since 2012. So newer hardware is UEFI.
Windows 7 normally was BIOS with MBR partitioning, so if upgrade from Windows 7 then probably BIOS/MBR, although Windows 7 could be installed in UEFI boot mode, if desired.

If old BIOS system, then you have to to use MBR for Windows as it only boots in BIOS mode from MBR.
Windows also only boots in UEFI mode from gpt.

If UEFI hardware better to use UEFI/gpt.
Windows 10 uses fast start up which sets hibernation flag & resets it with updates. Then grub will not boot Windows and you have to repair it. With UEFI you can directly boot Windows from UEFI boot menu to turn off fast start up or make other repairs. 

With BIOS, you have to temporarily restore a Windows BIOS boot loader to MBR, boot Windows & repair it, then restore grub to MBR to dual boot.  
You then need to always have a Windows repair flash drive and Ubuntu live installer for current installed versions. 

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

