---
title: "ASUS UEFI - Steady Black Screen"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by Laurence02 on 2013-10-13
Hi!
I am a (un)lucky owner or a ASUS K56CB (notebook) with Windows 8 pre-installed. I have burnt a Live CD and I can boot from it but when I press "Try Ubuntu" or "Install Ubuntu" I get a steady black screen. I have tried replacing (note: replacing) quiet splash with nomodeset. It did not work. I think the graphics card is the problem, and it is a Nvidia Geforce 740m. In the BIOS/Setup there is no option to switch off Secure Boot, only the "Secure Boot Control", which I don't know what it is. Lastly, I wish to dual boot Windows 8 and Ubuntu 13.04, so a step by step guide would be nice.

Thanks! And sorry if duped.

-Laurence

---

### Post by oldfred on 2013-10-13
Did you use DVD or flash drive. New versions are too large for CD and will not work correctly.
Does your system have dual video? And can you set which is used in UEFI/BIOS? 
Normally with nVidia nomodeset will get you into low quality video mode until you install nVidia drivers. But Intel may need different boot parameters.

Some other Asus
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
      
 Asus x55u UEFI change to BIOS
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)

---

### Post by Laurence02 on 2013-10-15
[COLOR=#000000]Did you use DVD or flash drive. New versions are too large for CD and will not work correctly. DVD[/COLOR]
[COLOR=#000000]Does your system have dual video? And can you set which is used in UEFI/BIOS? I have "Intel HD Graphics 4000". No option in BIOS.[/COLOR]
[COLOR=#000000]Normally with nVidia nomodeset will get you into low quality video mode until you install nVidia drivers. But Intel may need different boot parameters. Yes. Sorry, I would need that parameter.[/COLOR]

---

### Post by oldfred on 2013-10-15
I have posted these before for Intel and several have said they work, but I do not know which ones for which systems.

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

   Some other boot options
acpi_osi=Linux  acpi_backlight=vendor

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

