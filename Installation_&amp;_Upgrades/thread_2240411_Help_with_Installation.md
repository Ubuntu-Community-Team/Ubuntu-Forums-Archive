---
title: "Help with Installation?"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by kyle25 on 2014-08-19
I recently created a bootable flash drive with the Universal USB Installer to install Ubuntu onto my laptop. The first thing that pops up when I boot the drive, though, is GRUB. I'm using a 64-bit laptop and the newest version of Ubuntu. :/

---

### Post by fantab on 2014-08-19
Check the integrity of your downloaded Ubuntu.iso with either [MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM") or[ SHA256Sum]("https://help.ubuntu.com/community/HowToSHA256SUM"). If the match fails re-download the .iso.
Then reburn the .iso to USB: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by oldfred on 2014-08-20
If it is a new system, you do get grub menu booting in UEFI mode.
But if then a black screen it is a video issue and you may need nomodeset.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

