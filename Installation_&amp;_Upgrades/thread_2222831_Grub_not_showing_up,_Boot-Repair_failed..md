---
title: "Grub not showing up, Boot-Repair failed."
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by nathanajah2 on 2014-05-08
I'm trying to install ubuntu, alongside my freshly installed Windows 8.1.

The installation completed without any problem. However, when I rebooted, it booted straight to Windows.

I tried to use Boot-Repair, but it said that an error occured during the repair.

Here is the boot-info summary: [http://paste.ubuntu.com/7413633/](http://paste.ubuntu.com/7413633/)

---

### Post by oldfred on 2014-05-08
You have Windows in UEFI boot mode, but now have a Windows BIOS boot loader in the protective MBR. Windows will not then boot from that.

It looks like you installed Ubuntu in secure boot mode as you have signed kernels in grub menu list. But now have an empty efi partition sda3. It has no Windows efi boot files nor any Ubuntu efi boot files?

Your sda1 looks like a vendor recovery  and is now the only one with any efi files. sda2 is a Windows repair partition.

Best to turn off secure boot. Make sure fast boot is off in Windows. And Boot-Repair if booted in UEFI mode should add Ubuntu/grub's efi boot files to efi partition.
You will have to run Windows repairs or restore your efi files from your backup.

Lots more info in link in my signature.

---

### Post by nathanajah2 on 2014-05-09
Hi oldfred,

If I'm not doing anything wrong,

1. There is no secure boot settings in both Windows and my BIOS.
2. I have the "Secure boot is not configured correctly" message in my windows desktop.
3. When I ran repair, windows said that it can't find the problem.

---

### Post by oldfred on 2014-05-09
So is Windows booting in BIOS mode? 
I would not expect that.

And if a UEFI system, you must have a way to turn off secure boot unless one of the new 32 bit UEFI systems or an MS Surface. I think the Microsoft Pro can dual boot but not work too well.
What computer/model is this?

---

### Post by nathanajah2 on 2014-05-12
Windows is booting in UEFI mode according to msinfo32.

However, I can't find the UEFI firmware settings tile, and no settings in the BIOS as well.

My computer is a Sony VAIO SVS13118GGB, purchased around 2 years ago.

---

### Post by oldfred on 2014-05-13
A lot of other users with Sony and they seem to have issues. Not sure if any of these are similar, but usually vendors use the same UEFI/BIOS across several models with only adjustments for options. Main difference may be an Intel system vs. a AMD system.

 Sony Vaio & Ubuntu 13.10
 [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)
Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
 Sony SVE15125CXS Notebook  Only could Install in BIOS mode, Boot-Repair to UEFI dual boot works
[http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570](http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)
EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 on Sony Vaio S dual SSD
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)
Sony VAIO with Insyde H2O EFI bios Ubuntu 12.04 Dual Boot 
[http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html](http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html)
sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time installed 12.10, then  booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

---

### Post by nathanajah2 on 2014-05-13
The first link worked perfectly.
Thank you.

---

