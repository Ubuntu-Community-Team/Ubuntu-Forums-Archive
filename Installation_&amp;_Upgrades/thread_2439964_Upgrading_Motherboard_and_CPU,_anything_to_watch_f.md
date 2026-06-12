---
title: "Upgrading Motherboard and CPU, anything to watch for?"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by aridovah on 2020-04-03
My son and I are upgrading the motherboard and CPU, from an Intel Core 2 Quad to an i5-3570. The motherboard is going from a Dell lga 775 socket to a Dell lga 1155 socket in an own dell case. 
we are changing nothing else. We are running with a GT730 gpu that has been in there since I put it together. 
Any advice for us before we start seeing error messages? 
thanks everyone!

---

### Post by oldfred on 2020-04-03
My old system was a 2006  core2 (BIOS) and new 2014 UEFI system was a Haswell i5.
I converted from BIOS boot on gpt drives to UEFI boot on gpt drives. I had upgraded core2 system to small 60GB SSD in 2011 and that put off my upgrade until 2014, since core2 became so much faster.

I did have a GT720, since I made a mistake on motherboard. Old monitor had VGA & DVI in, but motherboard had HDMI & Display port out. So had to use GT720. My i5 Haswell had a faster video rating than the 720. Eventually found a HDMI to DVI cable and retired GT720 board.

With nVidia you will need nVidia boot parameter. You can turn off UEFI boot, turn on CSM/BIOS/Legacy boot and boot an old BIOS/MBR drive. But really better to convert to gpt and UEFI.

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

