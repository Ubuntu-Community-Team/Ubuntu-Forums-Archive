---
title: "Blank ssd when install in uefi mode"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by dumr on 2013-01-11
Hi. I have a problem. When I want to install ubuntu or mint both 12.10, when I get to the partition sizing, it gives me only 1 blank disk without any partitions on it. Second disk is recognized normally, and have partitions on it. On this first disk I have installed windows 8, which boot up normally. Live usb shows all partition normally but when I wan't to install it, disk is blank. But during install gives me option to install ubuntu allongside with windows 8. It's pretty confusing. I have bought new laptop asus k75vj 3 days ago, it's new computer after 4 and a half years so I am not very familliar with efi stuff :D

ty

---

### Post by oldfred on 2013-01-11
I do not think Mint has the new secure boot version of grub2 2.00? You also need the 64 bit version of Ubuntu.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Other Asus, may have same UEFI?
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
            ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

Is this an UltraBook as those have Intel SRT which somehow uses RAID?

---

### Post by dumr on 2013-01-11
uff thank you. It's the same for K55 and K75 it's basicly same laptop, but k75 is 17.3" and have 2 room for two hdd

---

