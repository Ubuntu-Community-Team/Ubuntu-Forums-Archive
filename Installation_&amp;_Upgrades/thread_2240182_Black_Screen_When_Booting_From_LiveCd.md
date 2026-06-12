---
title: "Black Screen When Booting From LiveCd"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by kevi123 on 2014-08-18
I'm trying to boot ubuntu 14.04.1 from a dvd. When I insert the dvd, go to the installation screen and click "Try ubuntu", I get a black screen and nothing happens (the display is on, just nothing on it). 
When I go nomodeset I get an error message on the ubuntu loading screen (can't read it because it is on a strange place of the screen), and then I get a glitched screen (noise screen), and finally - black screen.. 
I'm using an Acer Aspire V3-571G: hybrid graphics (intel and nvidia 630m) and intel i5 processor.
Help, Please! :)

---

### Post by oldfred on 2014-08-18
Are you booting with Intel or nVidia in use. Can you control that in UEFI/BIOS?

If the Intel chip you may need to use the other boot options to set size to match screen.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

Other Aspires, may be similar?

 acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

### Post by kevi123 on 2014-08-18
I don't know if intel or nvidia is in use.
 I am new and don't understand the advanced stuff. I have tried the nomodeset option and some of the UEFI options and it does not work...
I am thinking of trying another distribution, maybe mint.
By the way i've got windows 7 installed on the aspire and works perfectly.

---

### Post by kevi123 on 2014-08-20
I found a solution! :) Instead of booting from a live dvd I booted from a live USB (in NOMODESET) and for some magical reason it worked!!! :) :) :)

---

