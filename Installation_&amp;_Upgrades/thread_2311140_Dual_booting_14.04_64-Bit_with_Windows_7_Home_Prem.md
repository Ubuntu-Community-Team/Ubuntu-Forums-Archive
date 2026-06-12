---
title: "Dual booting 14.04 64-Bit with Windows 7 Home Prem 64-bit issues."
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by williambaldwin900 on 2016-01-24
Hello, I am having issues trying to dual boot my computer.

I have my windows 7 64 gaming PC here. UEFI is set to  UEFI Plus legacy. So I make a Ubuntu 64 14.04 USB stick and boot. Get to the  desktop just fine, and precede to install Ubuntu. So I go all the way  through, all works well and says it is complete, continue testing or  reboot. So I reboot and take the USB stick out, and it boots right into  Windows 7 every time...no GRUB menu or anything. Did Ubuntu NOT install  it? I did choose the install with Windows 7, and did the slider  partition manager where it said how much Windows vs Linux was. I gave Ubuntu 50 gigs. No go,  and not sure why.

---

### Post by yancek on 2016-01-24
You should do the resizing of a windows partition from the windows Disk Management tool.  You should also run chkdsk from windows after modifying partitions.  If you have windows 7 using UEFI, then you must install Ubuntu in UEFI mode.  Installing one system MBR and one UEFI results in either only one system being bootable or neither being bootable.  More info at the Ubuntu site below:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You might google and download the boot repair software and select the option to Create BootInfo Summary.  You can post a link to the output here and get some suggestions.

---

### Post by mastablasta on 2016-01-25
create the boto info summary using live USB: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

it could be that the GRUB was installed into wrong part of disk. you cnalso check with a live USB if the OS was installed well or not.

---

### Post by oldfred on 2016-01-25
If you have UEFI hardware, you should always boot in either UEFI or always BIOS/CSM/Legacy.
Some systems confuse it more, and require UEFI & Legacy mode to be on, but still let you choose which way to boot.

Most Windows 7 systems are BIOS, some UEFI. Default install from DVD is BIOS, but you can copy to flash drive & move files around so it can boot in UEFI mode.
Both Windows & Ubuntu install in same mode as installer is booted. So if you boot installer in BIOS mode, the your install is BIOS.
Windows only boots from MBR drives with BIOS. 
Windows only boots from gpt partitioned drives with UEFI.
Ubuntu can install in UEFI or BIOS boot mode from gpt partitioned drives.

So pick which way you want system to be configured - UEFI or BIOS and always boot in that mode. And make sure drive is partitioned with correct partitioning MBR or gpt for type of install you choose.

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

