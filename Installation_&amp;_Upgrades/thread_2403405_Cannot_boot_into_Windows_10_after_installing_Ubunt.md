---
title: "Cannot boot into Windows 10 after installing Ubuntu 18.04.1 LTS"
date: 2018-10-11
forum: Installation &amp; Upgrades
---

### Post by zelie.zazou on 2018-10-11
I am an **absolute beginner** with Ubuntu and Linux.

**Boot-Repair Report:** [https://paste.ubuntu.com/p/k3jKmFgqw9/](https://paste.ubuntu.com/p/k3jKmFgqw9/)

ASUS K75VM with 2 hard drives:
[LIST]
[*]sda with Win10 on sda1 
[*]sdb with Win7 on sdb1 (corrupted version that can't be used properly anymore) 
[/LIST]

After  installing **Ubuntu 18.04.1 LTS** on sda (sda8, swap on sda9, see 1st attachment) via a bootable USB, I couldn't boot on Win10 anymore  despite it was displayed on the GRUB. 
After using the command **sudo upgrade-grub**,  Win10 (/dev/sda1) vanished from the GRUB and was replaced by Win7  (/dev/sdb1). 
The Recommended Repair function of the **Boot-Repair software**  didn't bring Win10 back (see last attachment). 
Changing the **boot order in the** **BIOS**, replacing  Ubuntu by Win10 as the first boot option, didn't work either.
**Check Filesystem** used via the GUI did not reveal any damage on sda1.

More info in the attachments (fdisk -l report + error message when trying to open the Win10 windows folder via the GUI).

Thank you for reading my post and helping, if you can. Please ask me any additional info you would need.

---

### Post by oldfred on 2018-10-11
You cannot really mix BIOS/MBR & UEFI/gpt.
Grub only boots systems installed in same boot mode as once you start booting in one mode you cannot switch. It is possible to have different boot modes, but can then only boot from UEFI boot menu not grub. And boot mode on one drive must be consistent.

Windows only boots in BIOS mode from MBR partitioned drives like your sda.
Windows only boots in UEFI boot mode from gpt partitioned drives like you sdb.
Generally best to be consistent and have all drives in gpt and boot mode as UEFI with newer UEFI systems.

You also have a newer 4K drive, but the very old partitioning from XP. Start sector of 63 was used up to Windows 7. Then all new partitioning whether MBR or gpt used 2048 as start sector. Drive performance will be very slow if not set correctly.
[https://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
       [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by zelie.zazou on 2018-10-13
Thank you for your reply, now I have a better understanding of my problems.

However, I am still not sure what procedures I should try and implement to solve my boot issue. You suggested that I align my partitions, but would this allow me to boot on Win10 again or would it only increase the drive performance?

Could uninstalling Ubuntu from the sda drive solve the Win boot problem? Or could I try to repair the MBR from a Win10 bootable USB?

---

### Post by yancek on 2018-10-13
Your boot repair output shows that you have a Legacy install (msdos partitioning) of Ubuntu and although you have installed the Ubuntu EFI files from boot repair, that won't help.  You need to convert Ubuntu to GPT or re-install as a Legacy Grub will not boot an EFI windows.  See the Ubuntu documentation on converting at the link below below if you scroll down the page a bit.  The page also explains how to install EFI for a dual boot which may be simpler.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

As to booting windows as an MBR/Legacy install from windows 10, best check at a windows forum if you want to do that.

---

### Post by oldfred on 2018-10-13
Aligning drive will only improve performance of drive. Not related to boot issue as far as I know.
Unless partitions were changed.
Your Windows 7 on sdb, is now on gpt partitioned drive. Almost all Windows 7 installs are BIOS/MBR as DVD was BIOS only. DVD can be copied to flash drive & a few files moved/renamed to make it UEFI bootable, but few did that. And a few vendors started using UEFI with Windows 7 installs, just before Microsoft required UEFI boot of Windows 8, probably to make sure their UEFI worked.

Windows has start & size of its NTFS partitions in the partition boot sector or PBR which is like the MBR but for the partition. And that start & size must match the start & size in the MBR. Often can be fixed if not correct with chkdsk.
Always best to resize Windows partitions with Windows tools. Rule is Windows tools for Windows & Linux tools for Linux. Although some Linux tools may work on Windows.

UEFI strongly suggests you use gpt partitioning with UEFI installs. But Ubuntu installer is MBR, but both BIOS & UEFI bootable. 
So it looks like you may have installed Ubuntu in UEFI boot mode onto sda which is MBR, but installer found the ESP on sdb and put UEFI boot files into the ESP on sdb.

How you boot install media, UEFI or BIOS is then how it installs for both Windows & Ubuntu.

Just about impossible to convert Windows in place from one boot mode to the other. Or you have to backup data, totally reinstall if you want to convert to UEFI.
But not sure if reinstall may be easier as changing start from 63 to 2048 is a big change, and lots of repairs would at minimum be required using a Windows repair disk. 

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 
    
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by zelie.zazou on 2018-10-13
Thank you both for your replies and links, those help me much in understanding, and I hope ultimately solving my issue!

> Unless partitions were changed. 
Your Windows 7 on sdb, is now on gpt partitioned drive. Almost all  Windows 7 installs are BIOS/MBR as DVD was BIOS only. DVD can be copied  to flash drive & a few files moved/renamed to make it UEFI bootable,  but few did that. And a few vendors started using UEFI with Windows 7  installs, just before Microsoft required UEFI boot of Windows 8,  probably to make sure their UEFI worked.

I did not change partitions on my sdb. Sdb is my original drive that I bought with the laptop in 2012, and Win7 is my original OS. I must belong to those few cases of Win7 installed in UEFI boot mode. The reason might be that this laptop was quite expensive with very good specs for that time.

> UEFI strongly suggests you use gpt partitioning with UEFI installs. But  Ubuntu installer is MBR, but both BIOS & UEFI bootable. 
So it looks like you may have installed Ubuntu in UEFI boot mode onto  sda which is MBR, but installer found the ESP on sdb and put UEFI boot  files into the ESP on sdb.

I think you are right. I used the following commands: *[ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"* and *sudo parted -l* which confirmed that Ubuntu is installed in UEFI while the sda drive has msdos partitioning (attachements 1 and 2). Sdb, on the other hand, has gpt partitioning. That would explain why I can boot on my Win7, but not on my Win10. Furthermore, the information available in the GRUB location tab of the advanced options of the Boot-Repair software seems to confirm that the UEFI boot files were put into the ESP on sdb (attachment 3).

From the link yancek sent me, I found a procedure to convert Ubuntu from UEFI to Legacy mode using Boot-Repair ([https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode)). Could that possibly solve my boot problem? If yes, do I need to create a BIOS-boot partition? (My sda disk on which Ubuntu is installed is not gpt parted, so I shouldn't need to, but as the UEFI boot files are on the sdb drive which is gpt parted... hence my question).

---

### Post by oldfred on 2018-10-13
Windows 10 is not as dual boot friendly especially in BIOS boot mode.
It has fast start up/hibernation and turns that back on with updates. 
And if on, grub will not boot it. In BIOS mode you then have to temporarily install a Windows boot loader, fix Windows & then restore grub.
With UEFI you can always boot from UEFI boot menu.

You could add a bios_grub partition to your sdb drive and then install grub to it for BIOS boot and set UEFI/BIOS to boot in BIOS mode from sdb. You still can then boot Windows 7 in UEFI mode from sdb.
And keep a Windows boot loader in sda, so you can directly boot it without reinstalling boot loaders.

Long term, you may want to reinstall Windows & Ubuntu in UEFI mode on sda.

---

