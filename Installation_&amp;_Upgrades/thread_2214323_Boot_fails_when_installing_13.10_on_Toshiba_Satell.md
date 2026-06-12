---
title: "Boot fails when installing 13.10 on Toshiba Satellite P50-A-13N"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by immwi on 2014-03-31
Hi

I have Windows 8.1 preinstalled on a Toshiba Satellite and like to fully replace it by Ubuntu.

I'm booting Ubuntu 13.10 from a DVD 64bit.
In the BIOS I have secure boot switched on and UEFI enabled.
When restarting out of the BIOS I can start GRUB and select Ubuntu Installation or Live DVD.

The boot process fails here (see screenshot):
[ATTACH=CONFIG]251625[/ATTACH]

I verified MD5sum of the iso-file and the image-writer (windows internal) checked successfully the created disc.

I don't know how to proceed.
thanks, immwi

---

### Post by ubfan1 on 2014-03-31
Looks like a video problem, try the "nomodeset" addition to the linux line in the grub boot command (Add it by editing the grub command, type "e" to edit, instructions on screen. Once booted, you may have vendor proprietary drivers available.

---

### Post by oldfred on 2014-04-01
Not sure on Intel issue. Some have had better success with 14.04 even though it is not offical for several more weeks. Or you may have other issues/bugs. But Intel has included many fixes for its new processors in kernel, support software & video drivers that are now in 14.04.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio

---

### Post by immwi on 2014-04-02
GREAT! I added 
nomodeset
as boot-parameter. It did the trick!

Thanks a lot for your help!

best
immwi

---

