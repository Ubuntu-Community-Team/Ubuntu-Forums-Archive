---
title: "USB Installer not booting on skylake laptop"
date: 2016-07-18
forum: Installation &amp; Upgrades
---

### Post by nnvt on 2016-07-18
Hi!

I'm trying to install Ubuntu on my Asus Laptop (Model N551VW) with the following specs:

"Core I7 6700HQ (withIntel HD530)"

GTX960M 

Unfortunately the installer will not boot...

I booted verbose and the system had 2 start jobs running with no limit:

"A start job is running for Ubuntu Live CD Installer"
"A start job is running for Detect the availalbe GPUs and deal with any system changes"

eventually it will boot to the console but nothing can be done, if I try to start lightDM, Unity or XOrg it freezes and says this every 2 minutes:

"Task XOrg blocked for 120 Seconds"

Can anyone help me because I'm not sure what to do, never had any issues with getting the installer the boot on any of my laptops but this one won't boot.

---

### Post by oldfred on 2016-07-18
Many Asus have needed boot parameters. Often pci=nomsi
And those with nVidia also may need video boot parameters until nVidia driver is installed in new install. Usually nomodeset

Issues are often common by vendor as same or very similar UEFI is used.

 Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)
Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[URL="http://ubuntuforums.org/showthread.php?t=2303665"]http://ubuntuforums.org/showthread.php?t=2303665
[/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html) 
     Also shows Windows 8 screens or similar to Windows 10
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system
[/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710) 
    
I do not remember brand, but user switched in UEFI to use Intel video to boot, and then installed nVidia driver. Then he was able to turn on nVidia video.
But not all systems allow you to manual switch video.[URL="http://ubuntuforums.org/showthread.php?t=2303665"]
[/URL]

---

