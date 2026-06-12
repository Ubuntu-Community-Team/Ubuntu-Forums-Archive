---
title: "Trouble dual-booting Ubuntu and Windows 7"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by vsporeddy on 2014-06-10
This Lenovo G505s laptop came installed with Windows 8. I tried formatting that partition and installing Windows 7 x64 with a DVD but it wouldn't work because the disk is GPT. However, Ubuntu installed and worked perfectly fine. 

But I wanted Windows 7 so I converted the disk to MBR in Gparted, wiping everything, and made 2 partitions. On one I installed W7, and it is booting fine. On the other I installed Ubuntu, and it worked fine from the LiveCD, but after restarting _it just shows a blank dark purple screen_. The GRUB menu is working and I can choose Windows or Ubuntu.

Things I have tried:
adding nomodeset in the grub config
trying all combinations of legacy/EFI boot options in the BIOS
running boot-repair from the LiveCD 

Nothing worked. I'm sure the problem has something to do with either the graphics (this laptop has a weird AMD dual graphics thing) or some mismatch with EFI/BIOS booting. Any advice?

---

### Post by fantab on 2014-06-10
To install Windows7 on GPT disk you need to follow this [tutorial]("http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html").

You must Reformat your HDD as GPT, install Windows7 and install Ubuntu.

MBR is outdated, no need to go back to it. Stick with GPT and UEFI.

GPT stores a backup of itself on the HDD. When HDD is converted to MBR this backup table is still present and this confuses the installer.
You can also remove the backup table with [fixparts]("http://www.rodsbooks.com/fixparts/") and continue to use HDD with MBR.. though I don't recommend it.

---

### Post by oldfred on 2014-06-10
The Windows 7 DVD is BIOS install only, but you can copy it to a flash drive and do a few updates to make it a UEFI installer.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

If you have dual graphics, you may need other boot options. But do not know if any specific to AMD dual video:
      
 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

This Lenovo needed UEFI/BIOS update and it was a new system.

 Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)

Issues are often common across models by same vendor so some may apply?
      
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

 Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&

---

