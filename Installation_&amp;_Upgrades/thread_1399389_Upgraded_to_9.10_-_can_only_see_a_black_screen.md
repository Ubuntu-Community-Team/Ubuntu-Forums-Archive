---
title: "Upgraded to 9.10 - can only see a black screen"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by erakko on 2010-02-05
So I decided to upgrade from 9.04 to 9.10 today, I was quite sure there wouldn't be no problems. Well, at least not in the installation, and apparently the system works well too, but there's just one thing...

When I boot to the new kernel (2.6.31-19), it does show the new white Ubuntu-logo, but after it's gone, some text flashes through extremely fast, and after that the screen turns black, having two small and white horizontal lines on top of the screen. Soon after this, I can hear the login-window sound. I can log in by pressing enter, and then typing my password, and soon after I press enter again, I can hear the login sound. But still, the screen is black, having those same white horizontal lines on top of the screen, making the use of computer "quite" hard.

Right now I'm using the older kernel, but the problem is that the sounds won't work, the resolution is still low like when I had 9.04 (problems with Intel hardware), and CD's won't still be read when inserted into the CD-drive.

Here's my "lspci" in case someone wants to know of my hardware a little:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
09:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:04.1 CardBus bridge: O2 Micro, Inc. Device 7175 (rev 21)
09:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
09:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
09:05.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by 44Magnum on 2010-02-05
I'm a Ubuntu noob and was having the same problem this morning.

Upgrade worked for my Ubuntu-only machines, but my 2 Windows/Unbuntu systems only came up with grub-screens.

Searched all over and finally discovered that the problem is related to 'wubildr' file in the C:\ of my Windows system.  Downloaded the file from here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

and copied over the existing one in my Windows directory.... both my systems are running normally again.

Hope I can save you some of the grief, I went through.

---

### Post by erakko on 2010-02-05
> **44Magnum said:**
> Hope I can save you some of the grief, I went through.

I'm glad it worked for you, but I had a dual-boot system with Windows and Ubuntu last time about 3 years ago. So no, I'm pretty sure that won't help me... thanks anyway.

---

### Post by 44Magnum on 2010-02-05
I think you mis-understand.....

My Windows systems are both dual-boot systems (1 WinXP/Unbuntu, 1 Vista/Ubuntu).

Replacing that one file fixes the problem with Ubuntu not being able to find the Ubuntu system image inside the NTFS partition.

---

### Post by erakko on 2010-02-05
> **44Magnum said:**
> I think you mis-understand.....

My Windows systems are both dual-boot systems (1 WinXP/Unbuntu, 1 Vista/Ubuntu).

Replacing that one file fixes the problem with Ubuntu not being able to find the Ubuntu system image inside the NTFS partition.
Well now I don't understand...

I'm pretty sure that's fix for dual-boot system's problem, so how would it help me?

Besides, my Grub is okay, it's just that after the white Ubuntu-logo it goes black.

---

### Post by 44Magnum on 2010-02-05
> **erakko said:**
> Well now I don't understand...

I'm pretty sure that's fix for dual-boot system's problem, so how would it help me?

Besides, my Grub is okay, it's just that after the white Ubuntu-logo it goes black.

OK... so the mis-understanding was on my end then.  You are correct, that solution was for a dual-boot system.

Please ignore the noob with good intentions.

---

### Post by erakko on 2010-02-06
> **44Magnum said:**
> OK... so the mis-understanding was on my end then.  You are correct, that solution was for a dual-boot system.

Please ignore the noob with good intentions.
Well sorry, but I just can't see how that would help me at all.

---

### Post by erakko on 2010-02-06
Well, now I managed to get into the new kernel, but adding some changes in /boot/grub/menu.lst (I don't remember what it was exactly, something like adding "i915.modesomething=0" at the end of "kernel" and "kopt" lines).

But you could say I got back to the beginning. I sure hoped 9.10 would fix this problem with Intel-drivers, but of course it didn't fix it. Or I have just missed this update somehow... so now I have to still run this computer with vesa-drivers, which is fine, but I would like to finally get a solution for this problem.

When I change the "driver" option from "vesa" to "intel" in xorg.conf, after reboot, it tells me that the computer has to be run in "low-graphics mode". I've tried various xorg.conf configurations, and none of them has worked. Changing "intel" to "vesa" makes the "low-graphics mode" message disapear, and I can run the computer fine, just in "low-graphics mode", with low resolution and all.

I attached some log-files so it may come clear why this occurs.

---

