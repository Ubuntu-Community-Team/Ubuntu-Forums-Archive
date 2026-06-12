---
title: "Packard bell, UEFI , can't install, help!"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by burnsey2 on 2014-12-22
Hello.
I want to dualboot win 8.1 and ubuntu 14.10.

I have preinstalled win 8 , efi mode. When I boot my flash it shows - "usb hdd generic flash disk has been blocked by the current security policy".
Only way I can disable "Secure Boot" if I take "Legacy Bios". When I boot my flash via Legacy Bios it just shows me this "_(it blinks)" with black screen.

Help me, guys.

---

### Post by oldfred on 2014-12-22
Not seen many Packard Bells.
Have you updated UEFI/BIOS to latest version from vendor?
Once Secure boot is off, you then should have settings for UEFI or CSM(BIOS) as boot option. Flash drive should have two options, one UEFI and label of flash drive and the other just the label of the flash drive which is the BIOS boot.

What video chip does your system have. Do you get BIOS screen with tiny icons at bottom or grub menu?

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


 Packard Bell Easynote manually renamed bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

