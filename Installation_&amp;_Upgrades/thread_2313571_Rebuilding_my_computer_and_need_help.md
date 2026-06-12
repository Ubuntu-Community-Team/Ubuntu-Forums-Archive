---
title: "Rebuilding my computer and need help"
date: 2016-02-13
forum: Installation &amp; Upgrades
---

### Post by jsavga on 2016-02-13
Let me first say I'm getting older and with it am forgetting a lot of what I use to know.

I have a dual boot WinXP and Ubuntu 14.04LTS system. Windows XP is on it's own 1TB HD and Ubuntu is on a separate 1 TB HD. As far as I know the boot software (Grub?) is on the WinXP drive and that's the drive that boots and then I select Ubuntu and it boots it from the second HD. This system is getting pretty old and I've decided to replace the Motherboard(MSI Sli Plus), CPU (i5-6600), Video card (980ti), Memory (16GB DDR4) and install either Windows (new install Disc) 7 Pro or 10 Pro on a 850 EVO 500GB M.2 SSD and thus reformat the current Windows 1TB drive to use for storage. I would like to have a similar dual boot system and carry my Linux install on the second 1TB over unchanged. 

Here is what Gparted shows as my Linux Drive:
[IMG]http://i1154.photobucket.com/albums/p525/digphan/LinuxDrive_zpselom378u.png[/IMG]


I would like to know what problems I may run into with a Win 7 Pro install and what problems with a Win 10 Install for dual booting? Also How do I go about making my system dual boot again? What I'm really asking is how would I go about accomplishing this and making sure that the Linux system is kept intact and boot-able? What other problems may I run into?

-James

---

### Post by grahammechanical on 2016-02-13
If Grub is on the Windows drive (sda) then reformatting it will lose the ability to load Ubuntu. My solution would be to install Grub into the MBR of the Ubuntu drive (sdb) and tell the motherboard to boot from sdb.

```
sudo grub-install /dev/sdb
sudo update-grub
```

Do this before you reconstruct the machine. Write those 2 commands down somewhere as they will be useful later.

I have little experience with installing Windows but I am convinced that installing Windows 10 to sda will not only put a Windows boot loader on sda but the Windows installer will also put its boot loader in sdb as well. So, do not insert the Ubuntu drive in the machine until after you have installed Windows and then run those 2 commands again. The update-grub command is needed to detect the existence of Windows. But the grub-install command might not be needed.

Remember, the motherboard will need to boot from the Ubuntu drive to have options to load both Ubuntu & Windows but you can use the BIOS/UEFI to switch between drives.

Another problem to watch out for is if the new motherboard has UEFI and you install Windows in EFI mode. In this case Ubuntu should also be installed in efi mode. Which of course it will not be.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You should be able to switch between Ubuntu & Windows through the UEFI boot system. Or you might like to run Boot Repair which will put special Ubuntu efi boot files into sda efi boot partition to solve the problem.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards

---

### Post by oldfred on 2016-02-13
You can skip this post if sure you want BIOS/MBR. Just presenting the alternative as new hardware is UEFI.

While BIOS mode works in emulation on new UEFI systems, it generally is better to use gpt partitioning and UEFI. 
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You may not be able to stay at Windows 7. Microsoft is forcing all systems to update to Windows 10 and you have to change some settings to prevent it. Do not know details.

You can install Windows 7 in BIOS or UEFI boot mode, but Windows 7 default is BIOS. You have to copy to flash drive and move some files around to make it UEFI.
      
  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
Convert Windows 7 install to UEFI
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)

You can backup your /home, all data, and a list of installed applications. Then in a new install restore /home & data and easily reinstall apps from exported list. That is my normal backup so I can easily do a new install.

       
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

