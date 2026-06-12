---
title: "Unable to proceed with installation from liveUSB due to unresponsiveness"
date: 2019-02-06
forum: Installation &amp; Upgrades
---

### Post by whiterosee on 2019-02-06
I'm trying to install Ubuntu 18.10 alongside Windows on an asus Zenbook Pro (UX501V). When I boot from the USB the grub-like menu loads but when I start the OS to "try before install" after the desktop loads I'm unable to click on anything or type anything(not able to even open the terminal). After a while the cursor freezes completely and I'm unable to control it through the trackpad (only able to move it through touch screen but cursor still can't click on anything).

I have also tried to make a live usb with ubuntu LTS but the same problem persists. I also tried several programs to flash the USB (LiLi, Rufus, Win32 disk manager, Balena etcher).
Please help?

---

### Post by oldfred on 2019-02-06
Have you updated UEFI from Asus? Almost all systems need that whether installing Ubuntu or not.

Asus seems to need boot parameters.

This link shows multiple parameters with an older install, some may not be needed now, but you can experiment.
The encrypted install is a full drive LVM - logical volumes, not a dual boot type install, but boot parameters would be the same.
[https://roche.io/2017/04/ubuntu-1704-zenbook-pro](https://roche.io/2017/04/ubuntu-1704-zenbook-pro)

See link in my signature for general UEFI install info:

---

### Post by whiterosee on 2019-02-11
I'm still not able to get it to work through this method, hangs even before loading the desktop environment

---

### Post by oldfred on 2019-02-11
So you are booting, but have video issue?
Is this nVidia?

If nVidia you need nomodeset boot parameter, in addition to any others your Asus may need.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
You will need nomodeset to boot live installer and first boot or until you install proprietary nVidia driver from Ubuntu repository.

---

### Post by whiterosee on 2019-02-14
There isn't really a video issue, the desktop loads, it's just not clickable and after a while the cursor freezes (but I'm still able to move it with touch screen).
Yes I have nvidia graphics but this doesn't seem to be a related error. Also, few months ago I had installed Ubuntu LTS on this machine without any problem with the same USB stick.

---

### Post by whiterosee on 2019-02-14
[SOLVED]: incorrect partitioning of the USB drive, not enough space was being allocated to the ubuntu partition resulting in the files only partially being present. Fixed by manually removing all partitions of the USB drive and creating a new volume, then flashing again with the Ubuntu ISO.

---

