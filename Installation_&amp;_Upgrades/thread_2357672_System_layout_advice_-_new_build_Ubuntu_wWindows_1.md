---
title: "System layout advice - new build Ubuntu w/Windows 10"
date: 2017-04-04
forum: Installation &amp; Upgrades
---

### Post by ship22 on 2017-04-04
I'm building a new system using an ASUS Prime Z270 and utilizing the M.2 feature with a 250g mass storage board.. also have a 900g ssd. I would like to also duel boot windoze 10 along with the latest ubuntu.  I've been a *nix admin for 20 years so I'm fine with admin tasks but I've never used a m.2 device before. 

Any tips on how to lay this out partition wise and if sequence of installation will give me more or less grief when it comes to installing each OS and dealing with the boot partition? Grub and duel booting with windows seems to always be a pain in the rear the past couple of years.

Would really appreciate some pre-install wisdom.

Thank you!

---

### Post by TheFu on 2017-04-04
Windows first. Always.
I'm not big on dual-booting, much prefer virtualization, but I'm not a gamer. Clearly, Linux would be my choice for the hostOS. Should also say that I've never touched or even seen Win10.

---

### Post by ubfan1 on 2017-04-05
Dual booting Windows 10 and Ubuntu
Choose mode first, then maybe disk partition if an option (legacy case).

Mode    Disk Partitioning

UEFI    GPT -- The usual for Windows/Ubuntu dual boot
            500M EFI partition, both Windows and Ubuntu bootloaders fit easily in their own directories.
                Set /EFI/Boot/bootx64.efi as the fallback (a copy of either Windows bootmgfw.efi or
                Ubuntu's shimx64.efi (and grubx64.efi need to be present too).
            1M Grub-BIOS partition just in case you need a legacy install.
        
        MSDOS -- Not allowed for Windows


Legacy  GPT --  Need a 1M partition flagged grub-bios
                Put a 500M EFI partition for future mode change
        MSDOS -- Put a 500M EFI partition for future mode change

Look at SSD mfg. alignment recommendations for partition starts, 1M minimum.  

No need for /boot (Ubuntu kernels) unless you are encrypting the root.

---

### Post by ship22 on 2017-04-05
> **ubfan1 said:**
> Dual booting Windows 10 and Ubuntu
Choose mode first, then maybe disk partition if an option (legacy case).

Mode    Disk Partitioning

UEFI    GPT -- The usual for Windows/Ubuntu dual boot
            500M EFI partition, both Windows and Ubuntu bootloaders fit easily in their own directories.
                Set /EFI/Boot/bootx64.efi as the fallback (a copy of either Windows bootmgfw.efi or
                Ubuntu's shimx64.efi (and grubx64.efi need to be present too).
            1M Grub-BIOS partition just in case you need a legacy install.
        
        MSDOS -- Not allowed for Windows


Legacy  GPT --  Need a 1M partition flagged grub-bios
                Put a 500M EFI partition for future mode change
        MSDOS -- Put a 500M EFI partition for future mode change

Look at SSD mfg. alignment recommendations for partition starts, 1M minimum.  

No need for /boot (Ubuntu kernels) unless you are encrypting the root.

thank you! Is mode selection part of the windows 10 installation or ubuntu? Windows first, then Ubuntu install?

---

### Post by TheFu on 2017-04-05
Whether you use legacy BIOS or UEFI is a system-level choice (inside the BIOS).  I though that Win10 x64 required UEFI if you want GPT. Modern Linux distros should work with any combination of those 4 things. I've never used UEFI, even when given the choice. However, the Linux Foundation recommends using UEFI for security reasons.  I always choose GPT for physical installs if given a choice.

---

### Post by oldfred on 2017-04-05
Windows only boots using UEFI from gpt partitioned drives.
Ubuntu can boot with either UEFI or BIOS from gpt partitioned drives.
But you really want both systems in same boot mode, probably UEFI. And install Windows first, it like to have lots of extra partitions.

How you boot install media from UEFI boot menu is then how it installs.

If UEFI see also link in my signature.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Is M.2 standard or NVMe device?
I did not even know difference when I bought my M.2 drive for Z170 system, but happened to have standard not NVMe and still not sure if my motherboard could have used NVMe or not. Install then was just like any two drive install. Do not have Windows but multiple Ubuntus some on sda & some on sdb all in UEFI boot mode.

Older Asus have very similar UEFI screens to the newest. So some of issues may also be the same.
 Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)
Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Azus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)
BIOS only install Asus Z97-a
[http://ubuntuforums.org/showthread.php?t=2296538](http://ubuntuforums.org/showthread.php?t=2296538)

---

### Post by ship22 on 2017-04-06
The M.2 drive I have is NVMe. Once I booted my ubuntu installation flash in UEFI mode (as per the link you posted) I was able to create a uefi partition to boot from and it worked fine, even pulled in the windows partition as an option.

Thank you!

---

