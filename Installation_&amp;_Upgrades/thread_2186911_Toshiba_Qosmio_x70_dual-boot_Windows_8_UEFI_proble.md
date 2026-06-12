---
title: "Toshiba Qosmio x70 dual-boot Windows 8 UEFI problems"
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by Wrbhhh on 2013-11-09
Hi.

I can't boot the Kubuntu 13.10 from the DVD or an USB stick. Booting just freezes.

I've been looking at this thread hoping to make it work, but still no luck:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

When I try to boot, i get just a blank screen after selecting any option from the Grub menu (even to check disk).

I've been playing with editing boot options. When I removed splash and noquiet and add nomodest and set video=1280x1024-24@60, I was able to get some boot log data on the sreen. I took a photo when it froze, here it is:
[[IMG]http://i89.photobucket.com/albums/k223/Wrbhhh/th_IMG_20131109_225626_zpse74b47b9.jpg[/IMG]]("http://s89.photobucket.com/user/Wrbhhh/media/IMG_20131109_225626_zpse74b47b9.jpg.html")

Any help would be appreciated. If you need more data, just say so. Whoever helps me, you've got a beer. :)

---

### Post by oldfred on 2013-11-09
I cannot add much to what is in link as that is most of my knowledge. :)

What video card/chip does your system have. I see dual video in some specs?
So which mode does it boot in. nomodeset works for nVidia, but you need the other settings for Intel.

New Haswell systems also may need settings like this, even thought this was Toshiba.
       Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor

---

### Post by Wrbhhh on 2013-11-10
Yeah, that's the thing I don't get. I see drivers for both nVidia and Intel in the Windows 8 installation. When I first saw it, I was like WTF?! :confused: As I bought an aditional SSD drive and asked them at the store to install it and move my OS to it, I thought maybe they installed both drivers by mistake. I still don't understand why I have both. Does that mean I have two graphics cards? Why would I need two?

I'll try fiddling with these settings some more. I've already disabled my NIC and tried booting from USB. Secure boot was disabled when I got it from the store. I've also tried with these acpi_* options.

**EDIT:**

I also get these error messages right before GRUB apprears:
> Could not open "\EFI\BOOT\fallback.efi": 14
error: variable `root' isn't set.

---

### Post by oldfred on 2013-11-10
You have dual video. Intel builds video into most high end chips but not all motherboard use it. And then vendors add a higher end chip. The Intel uses low power to make laptop last longer and performance chip makes it work faster. Some auto switch on booting, others may have a setting in UEFI/BIOS.

 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

Have not seen that error. I might double check that down load was good with md5sum and install is good. You are using 64 bit verson? 
      
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Wrbhhh on 2013-11-10
The download is ok. I tried downloading it and burning it to the DVD twice (two different DVD discs). Also i tried it with an USB stick. The error is alwas the same (although it dissapears much quicker with USB booting, what is expected). I also validated the downloads and burns.

Yes, I'm using the 64-bit Kubuntu version.

---

### Post by oldfred on 2013-11-10
Google says it is related to secure boot.

See post #11
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1097570](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1097570)

[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/490605-toshiba-satellite-p50-uefi-w8-dualboot-cannot-install-12-3-nor-13-1-beta.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/490605-toshiba-satellite-p50-uefi-w8-dualboot-cannot-install-12-3-nor-13-1-beta.html)
Some get it to boot even with message.
[http://forums.partedmagic.com/viewtopic.php?f=4&t=80](http://forums.partedmagic.com/viewtopic.php?f=4&t=80)

---

### Post by Wrbhhh on 2013-11-13
I haven't been able to boot Ubuntu live DVD yet. For now I've installed it in VirtualBox. :(

---

### Post by manzana.granada on 2013-12-08
Hey, I have found an solution for this problem for the case of Linux Mint, there's a high chance that it would work in Ubuntu. See [http://forums.linuxmint.com/viewtopic.php?f=46&t=151949](http://forums.linuxmint.com/viewtopic.php?f=46&t=151949)

---

### Post by oldfred on 2013-12-08
Is this then what you did?

sudo Xorg -configure
sudo cp /home/mint/xorg.conf.new /etc/X11/xorg.conf
startx

Similar command in Ubuntu.
This backs it up.
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
The sudo xorg -configure creates a new one.

---

### Post by manzana.granada on 2013-12-09
Yes, but I have to use the boot option nomodeset to successfully reach the command line. Regards.

---

