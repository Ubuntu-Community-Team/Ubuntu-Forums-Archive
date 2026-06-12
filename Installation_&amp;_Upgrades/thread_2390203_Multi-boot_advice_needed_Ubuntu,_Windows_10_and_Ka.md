---
title: "Multi-boot advice needed Ubuntu, Windows 10 and Kali"
date: 2018-04-26
forum: Installation &amp; Upgrades
---

### Post by Roger_Williams on 2018-04-26
I'm looking at reloading my laptop. The laptop originally came with Windows 10 before I install Linux. The internal drive is 1TB so what I would like to do is install Windows 10 and Ubuntu 17.10 on the internal drive. Then install Kali Linux on an external SSD. I just need some opinions on the order to install, partition sizes, how hard it might be? I'm only installing Windows to be able to flash the bios of the laptop so I don't get stuck with ancient crap. So I was thinking 128GB for Windows 10, 400GB Ubuntu and the remainder for Data. What I've seen online says I should install Windows first since the Grub loader will recognize it and add it to the boot list. If it's going to be a major PITA to install Win10 alongside Linux then I'll just nix it and install the Linux distros.

---

### Post by oldfred on 2018-04-26
Newer UEFI or older BIOS?

If newer UEFI hardware, how you boot install media for both Windows & Ubuntu is then how it installs. And you want both systems installed in the same boot mode, both UEFI or both BIOS.
Many dual boot with Windows, but you must be sure to turn off Windows fast start up. 
See link in my signature below on Ubuntu UEFI install.

Do not know Kali and whether it is UEFI or BIOS. External drives in UEFI mode only boot from /EFI/Boot/bootx64.efi, but that file can be any boot loader with any distribution. BIOS installs still boot from MBR. Even newer gpt has a protective MBR that can be used for BIOS boot, but grub needs a bios_grub partition, if gpt partitioned & using BIOS to boot.

---

### Post by Roger_Williams on 2018-04-26
> **oldfred said:**
> Newer UEFI or older BIOS?

If newer UEFI hardware, how you boot install media for both Windows & Ubuntu is then how it installs. And you want both systems installed in the same boot mode, both UEFI or both BIOS.
Many dual boot with Windows, but you must be sure to turn off Windows fast start up. 
See link in my signature below on Ubuntu UEFI install.

Do not know Kali and whether it is UEFI or BIOS. External drives in UEFI mode only boot from /EFI/Boot/bootx64.efi, but that file can be any boot loader with any distribution. BIOS installs still boot from MBR. Even newer gpt has a protective MBR that can be used for BIOS boot, but grub needs a bios_grub partition, if gpt partitioned & using BIOS to boot.

It's newer UEFI hardware and I think Kali is BIOS. OK thanks so I need to figure out if I can get all of them to install in BIOS mode. Am I right about installing Windows first? I will check out the link in your sig and look up the fast start up thanks for the info.

---

### Post by oldfred on 2018-04-26
If Kali is going to be external so you have to go into UEFI/BIOS to select it anyway, I might still install both Windows & Ubuntu in UEFI boot mode.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by mircsicz on 2018-04-27
I'ld install first, has been like that since ages... Then grub (even in UEFI mode) will rec. Win and create an entry

---

### Post by Roger_Williams on 2018-04-27
OK thanks guys some reading to do over the weekend and I'll update when it's all done.

---

