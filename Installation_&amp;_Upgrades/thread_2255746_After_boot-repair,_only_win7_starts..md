---
title: "After boot-repair, only win7 starts."
date: 2014-12-07
forum: Installation &amp; Upgrades
---

### Post by Ondrej_Kamenicky on 2014-12-07
I bought Lenovo Thinkpad E531 with win8. Installed win7 instead win8. 
I want to have dual boot win7/ubuntu so i installed ubuntu 12.04.
After installation only win7 booted up, so i tried boot-repair with no help.
"bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi" didn't help either.

[http://paste.ubuntu.com/9412730/](http://paste.ubuntu.com/9412730/) 

btw i'm new to linux.

---

### Post by yancek on 2014-12-07
Did you try the suggestions at the bottom of the boot repair output?  Starting with the line below there are several options to try.

> Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

---

### Post by Ondrej_Kamenicky on 2014-12-07
Yes, i tried "bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi" in cmd, it said "operation completed successfully" but still boots just win7

---

### Post by oldfred on 2014-12-07
You need to either go into UEFI and set ubuntu entry as first, use one time boot key often f10 or f12, or with the bcdedit, you should be able to choose in Windows boot a one time reboot into Ubuntu. 

Do you get errors on the ubuntu boot?
Some have video issues, what video card/chip does your computer have?
Some with Lenovo just needed to set screen brightness up 


I thought 12.04 was now 12.04.5
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Since you have new hardware, you probably will have better success with newer versions of Ubuntu. New kernel, support software & video drivers all work together and are in the newer versions.

With 14.04 you get long term support, but 14.10 has many fixes and updates for the newest hardware.
[https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install](https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install)

Many other Lenovo, not sure if similar or not:
 [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)
Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12

---

### Post by Ondrej_Kamenicky on 2014-12-07
i dont have the option to change entry boot order in UEFI, in bcdedit i cant tell which one of those entry is ubuntu

i used 12.04.3 becouse it is certified on my laptop
[http://www.ubuntu.com/certification/hardware/201304-13465/](http://www.ubuntu.com/certification/hardware/201304-13465/)

brightness is on max
video card: NVIDIA GeForce GT740

maybe this will help: when i change  in bcdedit path to \EFI\ubuntu\grubx64.efi after restart its back to \EFI\Microsoft\Boot\bootmgfw.efi

---

### Post by Ondrej_Kamenicky on 2014-12-07
Ok, i found it. In bios i had lock boot order enabled. Thanks for help

---

