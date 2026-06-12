---
title: "LiveUSB will not Boot on Lenovo v570"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by zaa526 on 2014-06-09
[COLOR=#333333][FONT=UbuntuRegular]I have a Lenovo v570 that I'm trying to do a clean install of trusty on and for the life of me I can't find any way to get it working. When I try to boot from the SD card it's on, it doesn't even list it in the boot menu and the SD card is the first one listed on boot order. I installed it from 'Startup Disk Creator' from another device with trusty but still no luck. I've heard that there are a lot of problems with UEFI, which I'm guessing is the issue here but when I go into the BIOS, it mentions nothing about UEFI. I've tried different USB sticks, SD cards, DVDs, and CDs but still no luck. Does anyone know how to fix this?[/FONT][/COLOR]

---

### Post by oldfred on 2014-06-09
Someone with Lenovo posted this a while back.

 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

      
 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)


 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

 Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)

---

