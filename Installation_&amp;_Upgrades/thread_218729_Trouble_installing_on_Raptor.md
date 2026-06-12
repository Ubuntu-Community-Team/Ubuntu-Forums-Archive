---
title: "Trouble installing on Raptor"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by tuxboxxer on 2006-07-19
I'm attempting to install Ubuntu on a WD Raptor 36GB. I have a Gigabyte 7NNXP motherboard with a Silicon Image 3112 controller on it. I had no problem configuring this to work in my previous Linux install with Gentoo. For some reason, the kernel is not configured right on the livecd and it doesn't recognize the drive at all. Does any one know of a way to fix this so that I can install on it? Thanks.

---

### Post by zxee on 2006-07-19
I don't know what the problem is. It looks like the controller is supported in the latest kernel. [http://linux-ata.org/driver-status.html](http://linux-ata.org/driver-status.html).
I believe there's a way to step through the install instead of doing the automatic installation. Look again at the options at the installers start up screen. You might also consider trying knoppix-at least to see how that distro solves the issue.

---

### Post by tuxboxxer on 2006-07-19
I figured out the problem. Apparently it wasn't the raptor at all. I had a usb flash card reader hooked up without a flash card in it and the system was getting confused. Once I disconnected that, it read all of the drives fine. Thanks again.

---

