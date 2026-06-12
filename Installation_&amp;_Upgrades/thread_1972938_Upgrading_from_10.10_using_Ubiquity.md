---
title: "Upgrading from 10.10 using Ubiquity"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by Middlerun on 2012-05-04
I've been using 10.10 on both my desktop and my laptop. I figured it's time to get up to date so I made a bootable USB drive to upgrade my laptop with. I was going to do a fresh install, but when I ran the Ubiquity installer it gave me the option to upgrade my 10.10 install to 12.04 and keep all my files and installed applications. It worked perfectly! So, I can do the same thing on my desktop right? Well for some reason when I try to do it on my desktop, that option just doesn't show up. The only options I get are install side-by-side, fresh install or "something else" (i.e. manual partitioning). No upgrade option. I'm using the exact same USB drive that I used to upgrade my laptop. I think maybe it's because I'm dual-booting with Windows. Is there any way I can get this to work like it did on my laptop?

---

### Post by grahammechanical on 2012-05-04
I cannot test this out as I do not have a USB drive but when in 11.10 on the desktop try just plugging the USB drive in. Do not boot from the USB drive. See, if 11.10 detects that there is an ISO image on the drive and may be it will notice that the image is of a later version than 11.10 and offer to upgrade from it.

Regards.

---

### Post by Middlerun on 2012-05-05
Nah, I tried that, no dice. FYI I think the same thing would be happening using a CD, I only used a USB drive because my laptop has no CD drive.

The key seems to be that I'm dual booting on my desktop, I think if I could find a way for the installer to not see the Windows partition maybe it will work then. But I'm not sure if that's even possible without erasing my Windows install which I don't want to do.

---

### Post by darkod on 2012-05-05
No, the key seems to be whether you have internet connectivity or not. Few people have mentioned it here on the forum.

I guess during the upgrade it will need some files off the internet so it gives you that option only if you are connected.

Boot your desktop with the usb, into live mode, make sure you have internet connected. Then click on the Install Ubuntu 12.04 icon and you should have the upgrade option.

If you have problems making the internet work, tell us with more details what is going on. In most cases the wired internet should work in live mode 99%.

---

### Post by Middlerun on 2012-05-05
The internet connection works fine, I'm posting this from within the LiveUSB environment. Still no upgrade option.

---

### Post by Middlerun on 2012-05-26
Well, I seem to have solved the problem, in an unexpected way. I eventually decided to make a new partition, install 12.04 alongside 10.10, copy all my stuff over, then once I had 12.04 set up, delete the old partition. However after deleting an old HFS (hackintosh) partition and moving/resizing the 10.10 partition to make room on the disk, when I ran the installer suddenly the upgrade option was there. I'm not sure why it works now when it didn't before, my guess would be that the installer gets confused by HFS partitions.

---

