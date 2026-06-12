---
title: "Problems with instaling GRUB2"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by Nico_Grndel on 2014-05-24
Hi Guys,
I am kind of a Linux newbie, and i just wanted to install Ubuntu alongside windows 8.1 on my Lenovo Ideapad y500. After burning the ISO to a stick and booting from it, I had my first Problem: after the purple Splash Screen i only saw a blinking white cursor. As it didnt go away, I tried pressing some buttons, and noticed, that if i press the left and the right Arrow Keys, my PC played a sound. After retrieing to boot from the disk over and over agaqin, I somehow pressed the Escape key on accident during the splashart and i could select my language and select, whether i want to install Ubuntu, try Ubuntu and several other things. After pressing Install Ubuntu it was the same as before: Black screen, blinking cursor and sounds when i pressed the left and the right Arrow Keys. So I tried every single Option, until i figured out i had to use nomodeset. After that worked, i could finally instal Ubuntu. The installation process was completely normal, but after a while, an errormessage popped up: >>grub install/dev/sda<< failed.This is a huge Error. (Translated from German ;)). I suspect the problem is that sda is the SSD, which Windows uses to boot faster. There is nothing i can read with Windows on that Disk and its a unknown Formatation. It gets used by Intel Rapid Technology. I think the Computers MBR is on that Drive, or at least, thats what it looks like. Can anybody help me with this Problem? I realy want to install Ubuntu, WIndows has such a high RAM usage since a couple of weeks!
In best Regards,
Nico Gründel

---

### Post by ubfan1 on 2014-05-24
Take a look at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
The new machines with Windows 8+ preinstalled are all UEFI, and come with gpt partitioned disks, which means you can't even install grub to the MBR anymore without making another 1M partition with the grub-bios flag.  Stick with the grub-efi, which works within the UEFI framework, and allows you to keep the Windows bootoaders as well.   From the Windows side, turn off things which short-circuit the boot process, like the power options for fast boot.  From the UEFI Settings/BIOS, give yourself a "normal" vs a "fast" boot speed (or a non zero value if possible).

---

### Post by oldfred on 2014-05-24
Usually you have to turn the Intel SRT off as that confused grub install. The SRT uses RAID and installer is not set to install to RAID nor should it in your case.

 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

Slightly different models, but may be similar issues.

  lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

### Post by Nico_Grndel on 2014-05-25
Just if anybody wonders, i solved my Issue: I always starter in not EFI Mode but in Legacy Mode, because when I tried to boot the cd in EFI mode, I have always gotten an Error anthen when I tried to Install or test Ubuntu, the Monitor just was black. I know found what i had to do, propably because i have 2 Graphics card with SLI: I had to add following Options when pressing e in the menu:
[COLOR=#000000]nomodeset[/COLOR]
[COLOR=#000000]acpi=0[/COLOR]
[COLOR=#000000]acpi_osi=linux[/COLOR]
[COLOR=#000000]acpi_backlight=vendor[/COLOR]
[COLOR=#000000]noalpic[/COLOR]
[COLOR=#000000]i915.i915_enable_rc6=1[/COLOR]
[COLOR=#000000]video=1280x1024-24@60[/COLOR]
[COLOR=#000000]video=VGA-1:1280x1024-24@60[/COLOR]

---

