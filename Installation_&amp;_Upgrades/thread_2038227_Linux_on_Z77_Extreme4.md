---
title: "Linux on Z77 Extreme4"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by bv_andy on 2012-08-06
Hello,


Just a warning: I am a complete noob to Linux. (As long as everything goes right I am an expert though)


First Specs:
Asrock Z77 Extreme4 BIOS 1.80 (updated to 2.0 -no change)
i5-3570k (OC:4.5 - but I tried without overclock and still no luck)
ATI HD 7970 Saphire
SSD Corsair Force GT 120Gb - latest firmware
HDD WD WD5000AAKS
2x4Gb DDR3 Samsung 1600Mhz Low profile (I had 2x2Gb OCZ something before, same difference)


I've been trying to boot Ubuntu 12.04 for quite some time now but with no luck. (this from both CD/USB drive from different downloads, including alternative)
I've tried to start with the F6 "Other Options" and only managed to get some text which I took a photos[ LINK]("http://imgur.com/a/XcOx1"): 

1st picture with normal bios settings
2nd: with legacy bios
3rd and 4th can't even remember how I got that far.

I have also tried Fedora with no luck.

Any help would be appreciated.

Edit: turns out Linux doesn't support having anything on the "ASMedia ASM1061" SATA controller. Moving my DVD-RW on one of the Panther Point connections solved the problem and was able to boot both in UEFI mode or normal, and both from CD and USB.

---

### Post by oldfred on 2012-08-06
You have UEFI which complicates things a bit. Most UEFI systems also let you use BIOS mode, but if dual booting need to make sure everything is installed in the same mode.

Do you have Windows already installed or installing to bare drives?

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

Someone also posted this:
> AsRock calls BIOS mode AHCI.
"Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.


---

### Post by bv_andy on 2012-08-06
thanks for the reply. Turns out that was exactly the problem. I found out by removing all the SATA and connecting them one by one. And thanks for the links. I am looking forward to learning how to master UEFI.

---

