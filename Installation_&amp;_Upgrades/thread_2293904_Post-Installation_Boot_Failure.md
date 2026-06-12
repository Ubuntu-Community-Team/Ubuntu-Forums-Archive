---
title: "Post-Installation Boot Failure"
date: 2015-09-08
forum: Installation &amp; Upgrades
---

### Post by Gregg_Johnson on 2015-09-08
I have recently put together a new pc. I went to install Ubuntu 14.04. The installation went fine nothing seemed to go wrong. Wen I restarted the system afterwards I can Ubuntu is installed, but when I try and boot into it all I get is a screen with a blinking underscore. I can't type anything in the screen and after +10 minutes the screen doesn't change. 

I'm not sure what I can do. I tried browsing the internet for similar problems but couldn't really find anything.

Any help will be much appreciated.

Thank you,
Gregg

---

### Post by yancek on 2015-09-08
If you accepted the defaults during the installation, everything should have worked especially since this is the only operating system.
You could try booting the Ubuntu install medium again, select the Try Ubuntu and go to the Desktop, open a terminal and type the two commands below consecutively, save the output and post here.  If that doesn't provide enough info, you may need to get boot repair and run that.  

```
sudo fdisk -l
sudo parted -l
```

That is a Lower Case Letter L in both commands.  The blinking cursor usually means improperly installed bootloader.  The link to boot repair below.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Gregg_Johnson on 2015-09-08
The same screen appears with the blinking underscore if I select the "Try Ubuntu without installing" option.

So, I'm unable to get to a terminal to get you the output.

---

### Post by oldfred on 2015-09-08
Also what motherboard & video card/chip are you using?

---

### Post by Gregg_Johnson on 2015-09-08
Gigabyte GA-Z97-HD3 motherboard, intel i5-4590 cpu, EVGA GTX 960 graphics card.

---

### Post by oldfred on 2015-09-08
Gigabyte has issues with IOMMU.
And nVidia needs nomodeset boot parameter in grub menu to boot.

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

After you install you also need nomodeset until you install the correct nVidia driver. Do not use a driver directly from nVidia.
If only Ubuntu installed, and  UEFI, you need to press escape to get grub menu.
If BIOS you hold shift key from UEFI until menu appears. You will need fast boot off in UEFI or it boots too fast to press a key.

---

