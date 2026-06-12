---
title: "Best method upgrading hardware"
date: 2017-01-18
forum: Installation &amp; Upgrades
---

### Post by warwickben on 2017-01-18
I plan to swap out my mother board only for a better model that is more capable . 

I currently have a dual boot setup . Ubuntu on one ssd, windows 10 on a second ssd.  Then a 1t hdd I have split  partion for files etc . 

Would the best way to just transfer any thing I want to the hdd and just start from scratch on the two ssd's I use for booting ?

---

### Post by oldfred on 2017-01-18
New motherboard will be UEFI, but have CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

So if current drives are in the 35 year old BIOS/MBR configuration you can use them.
But there are some advantages to UEFI/gpt.

At the minimum I would convert Ubuntu drive to gpt, reinstall & restore /home & other settings from backup. Ubuntu can boot in either UEFI or BIOS from gpt.
If UEFI you need the ESP - efi system partition & if BIOS on gpt you need the bios_grub partition. I typical add both partitions to all new or reconfigured drives including larger flash drives whether currently just data or a full install.

But you want both systems booting in same boot mode, either both UEFI or both BIOS.


 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

