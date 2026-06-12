---
title: "New computer, can't properly install any 64 bit Linux operating system"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by Panderz on 2013-07-31
I just got finished building my new computer and I can't get any 64 bit version of Linux to work. When I try to install 64 bit Ubuntu, my mouse does not work and the install fails when I just try to use the keyboard to install, an error with making the swap space occurs. I went ahead and tried to install the 32 bit version of Ubuntu, it installed without any problems. However, the 32 bit desktop is really slow, the command top is showing around 200% cpu usage. I also tried 64 bit Open Suse (12.2) and 64 bit Debian (7, wheezy). The exact same problem with the mouse occurs, it's just as though the mouse isn't plugged in. With lsusb in the live version of 64 bit Ubuntu, it doesn't show my mouse, though my keyboard works just fine and shows up.
It's not a hardware problem, my mouse works just fine in the bios and in Windows. I thought that maybe my install device was corrupt, so i reinstalled the 64 bit version onto a fresh cd, still the same result. Also, instead of the nice graphical interface that usually shows up when booting to a live cd, where it shows "try ubuntu" or "install ubuntu", it shows a grub like screen with a black backdrop instead of purple.
My cpu, in case you need to know, is an amd fx-8350 vishera.
Please someone help me, I'm really missing being able to use Ubuntu.

---

### Post by oldfred on 2013-07-31
If you are getting a grub menu on booting the installer you are booting in UEFI mode not BIOS mode. That should be fine, but some systems have not resolved all the UEFI issues. Have you updated UEFI/BIOS to newest version?
But some UEFI have many issues, and then you may be able to install in BIOS/CSM/Legacy mode. If not installing Windows you can still use gpt partitioning, but Windows will only boot from gpt partitioned drives with UEFI. Ubuntu can use BIOS or UEFI to boot from gpt partitioned drives. If dual booting you need to have both systems in the same UEFI or BIOS mode. If you installed with the 32 bit version that was BIOS mode only as the UEFI files are only in the 64 bit versions.

My older motherboard had BIOS settings for USB keyboard and mouse. Windows & Ubuntu seemed to have drivers but grub and installer seem to use defaults which relied on BIOS settings.

---

### Post by Panderz on 2013-07-31
That seems as though that might be the problem, I'm a little weary of updating bios/uefi after having heard some horror stories of bricked motherboards. I guess I'll try though, not much choice. I'll let you know how it goes.

---

### Post by Panderz on 2013-07-31
Okay, I found the problem and the answer was located here -> [http://askubuntu.com/questions/281964/live-os-doesnt-see-usb-mouse-or-keyboard](http://askubuntu.com/questions/281964/live-os-doesnt-see-usb-mouse-or-keyboard)

I just enabled IOMMU and now all of my usb devices are able to be used on the 64 bit version. Cheers!

---

