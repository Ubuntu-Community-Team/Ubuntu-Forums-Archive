---
title: "Can I upgrade bios mobo to uefi mobo and not have to re-install anything"
date: 2017-11-02
forum: Installation &amp; Upgrades
---

### Post by two4two on 2017-11-02
I couldn't find anything on here that is like this question so I am asking it.  Please forgive if it is a duplicate.  Also I know it might not be exactly germaine, but I hope someone will answer.  I have an older dual-boot computer with 2 IDE hard drives and one SATA hard drive.  On sda/sda1, an MBR IDE drive, there is WinXP.  On sdb/sdb1, the other MBR IDE drive, is Ubuntu.  I want to upgrade the Mobo/CPU,etc, and the new Mobo will be UEFI.  Can I do it and the Mobo will recognize that I have IDE/MBR drives and boot up OK?  I know WinXP is old.  I'll take care of that after the upgrade.  Maybe Win7.  It is the Ubuntu that I will mostly use.  Also I will upgrade that to 16.04.1 after the upgrade.  I guess my question is do these mobos sense what kind of disks you have an automatically adjust and boot up using my hard drives as they are?.

---

### Post by oldfred on 2017-11-02
UEFI has this, most vendors still call UEFI as BIOS, but have settings to turn on or allow BIOS/Legacy/CSM boot.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

I converted to using gpt partitioning in 2010 in BIOS boot mode. When Windows started making UEFI standard, I added an ESP - efi system partition to all new or reformatted drives for future use with UEFI. Then it made it easier to convert drive from MBR(msdos) to gpt(GUID).
UEFI uses gpt partitioning as its standard. 
Windows 64 bit only boots in UEFI mode from gpt.
Windows only boots in BIOS mode from MBR.
So drive partitioning has to match Windows install.

Better to start converting to UEFI/gpt if you have new UEFI hardware. BIOS/MBR goes all the way back to the original PC, so 35 years old.
      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by rbmorse on 2017-11-02
The new motherboard will have to have a physical interface for the IDE harddrives (40 pins?).  Good luck.  You can probably access the data on the IDE drives using an IDE to USB converter connector, but whether you will be able to boot the system from one of the drives using such a converter is anyone's guess.  I'd be prepared to do clean installs of the operating system(s) onto the new system (not a bad practice, anyway, especially for a Windows system). 

The MBR/UEFI partitioning issue should not be a problem as long as the new motherboard UEFI (what used to be the BIOS) has support for MBR Legacy mode.  Most Intel/AMD chipset-based consumer grade motherboards do. 

The real hurdle you face will be to find a new motherboard with an IDE interface.

---

### Post by two4two on 2017-11-02
> **rbmorse said:**
> The new motherboard will have to have a physical interface for the IDE harddrives (40 pins?).  Good luck.  You can probably access the data on the IDE drives using an IDE to USB converter connector, but whether you will be able to boot the system from one of the drives using such a converter is anyone's guess.  I'd be prepared to do clean installs of the operating system(s) onto the new system (not a bad practice, anyway, especially for a Windows system). 

The MBR/UEFI partitioning issue should not be a problem as long as the new motherboard UEFI (what used to be the BIOS) has support for MBR Legacy mode.  Most Intel/AMD chipset-based consumer grade motherboards do. 

The real hurdle you face will be to find a new motherboard with an IDE interface.


I have PCIe ide/SATA controller card into which I plug my IDE drive.  Hopefully the Mobo bios will detect them thru this card.

---

### Post by ubfan1 on 2017-11-02
I had a sata to ide disk caddy on an older laptop, and found grub would hang on accessing the caddy (which was before the internal hard disk in boot order).  Putting grub on a USB which could be put before the hard disk allowed grub to run, and then it could boot a root filessytem from the caddy.

---

### Post by grahammechanical on 2017-11-02
To confirm what has already been stated

> For [backward compatibility]("https://en.wikipedia.org/wiki/Backward_compatibility"),  most UEFI implementations also support booting from MBR-partitioned  disks, through the Compatibility Support Module (CSM) that provides  legacy BIOS compatibility.[SUP][[36]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-arch-forum-uefi-mbr-37")[/SUP] In that case, booting Linux on UEFI systems is the same as on legacy BIOS-based systems.




[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Oh, for future reference, we do not mind if you are asking a question that has previously been asked. We do prefer people to create their own thread. The problems might not be exactly the same and there may be differences in hardware.

Regards

---

