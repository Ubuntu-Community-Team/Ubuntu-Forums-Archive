---
title: "Can't install ubuntu in my new ideapad u430"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by mortemdei on 2013-09-21
I just got my new laptop, a lenovo ideapad u430, but I can't install ubuntu. I'm not a complete noob, I've installed ubuntu in other computers before, but this one is giving me problems. I got it to boot from the usb but the first installation screen is barely visible, very, very dark, and nothing seems to work. If I press enter when the orange screen with the small keyboard logo appears, it gives me a menu to either install or use ubuntu, but if I choose any of the options it tries to start and then just freezes and the screen is either black or show some logs of what it was doing. Please help, I don't want to have to use windows!

---

### Post by mikewhatever on 2013-09-21
Which version of Ubuntu have you tried installing? Also, some hardware specs would have been nice.

---

### Post by mortemdei on 2013-09-21
I'm trying to install the 13.04, the 12.04 version sort of works, but doesn't recognize the  wireless. If I install it and then install the latest kernel will that  fix the wireless problem? or should I keep trying to get the 13.04  working?

The specs are in this page [http://www.notebookcheck.net/Review-Lenovo-IdeaPad-U430-Touch-Ultrabook.100623.0.html](http://www.notebookcheck.net/Review-Lenovo-IdeaPad-U430-Touch-Ultrabook.100623.0.html)

---

### Post by mikewhatever on 2013-09-21
You should probably be using a [daily image of 13.10]("http://cdimage.ubuntu.com/daily-live/current/") for Intel's Haswell support. 13.04 will never get it, and 12.04 will have, when xorg is backported from 13.10.

---

### Post by mortemdei on 2013-09-21
I tried booting a 13.10 usb but I got the same black screen of sadness. It seems that it might be a kernel issue(?), because ubuntu 12.04 worked untill I upgraded the kernel, and the recovery system works with the 3.2 (more or less). I guess I could reinstall 12.04, but I would be stucked with the 3.2 kernel, which is not very desirable to tell you the truth. What can I do?

---

### Post by mikewhatever on 2013-09-21
Not sure. The machine is so new, there seems to be no info yet about its Linux compatibility.

---

### Post by oldfred on 2013-09-21
Some others:
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

I might try the same settings
acpi_osi=Linux acpi_backlight=vendor

Some with Intel graphics needed this:

 video=1280x1024-24@75 or whatever native resolution is

Some other similar (?) lenovo

 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)

If you have an Ultrabook you will also have issues with Intel SRT and its RAID interfering with grub installing and dual video. See link in my signature.

---

### Post by mortemdei on 2013-09-21
Your answer is a bit confusing. The usb boots just fine, I even get the purple screen with the little icon at the bottom, if I press enter I even get a selection screen in a sort of text mode, the problem is after that. When I chosse install or try ubuntu I get a blackscreen! I already disabled secure boot and erased windows, so it is unlikely to be a windows-linux compatibility problem (I think).

---

### Post by oldfred on 2013-09-21
Purple screen at bottom is BIOS mode, is that how you want to install?

If recovery mode works then that has nomodeset as default. You can look at its settings with e on grub menu.

Shows both BIOS & UEFI boot screens.
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by noah-azpiri on 2013-09-23
I had the same problem until I realized that the screen brightness was 0 during installation. Try to rise the brightness with F12.

---

### Post by mortemdei on 2013-09-23
Thank you so much, now I feel very silly. It was the brightness indeed. I'm marking this a solved.

---

### Post by skipcoombe on 2014-09-01
> **mortemdei said:**
> I just got my new laptop, a lenovo ideapad u430, but I can't install ubuntu. I'm not a complete noob, I've installed ubuntu in other computers before, but this one is giving me problems. I got it to boot from the usb but the first installation screen is barely visible, very, very dark, and nothing seems to work. If I press enter when the orange screen with the small keyboard logo appears, it gives me a menu to either install or use ubuntu, but if I choose any of the options it tries to start and then just freezes and the screen is either black or show some logs of what it was doing. Please help, I don't want to have to use windows!

Hi mortemdei,

You are more skilled than me.

I can't get "USB media" to display on my boot options dispite disabling secure boot and enabling USB boot (only windows and network boot options display).

I'd appreciate any advice about your success.

Skip

---

