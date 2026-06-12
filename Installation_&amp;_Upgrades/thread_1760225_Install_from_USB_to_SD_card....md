---
title: "Install from USB to SD card..."
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by cjohnsonuk on 2011-05-16
I'm trying to install Ubuntu Server 11.04 to my EEEPC701 to use it as a local web server to test out some web based apps.  Its got 2Gb ram but only 4GB of disk space.  I'm currently installing it with 3GB partition mounted at / and 1GB for swap.  All worked well with the default installation but I ran out of disk space when installing the apps so rather than the default 2GB for each partition I've gone with the 3gb/1gb split as above.

However the issue I'm trying to sort is that it won't let me install to the 16GB SDHC card installed in the internal card reader, its just not showing at all in the partitioner.  My install media shows up in the bios boot choice menu along with the "internal card reader" ( the one I want to install to) and the internal 4GB drive.  It also takes ages to run the install (about 20 minutes longer than when I run it with the 16GB drive removed from the internal reader.

Installing to the SD card means I can swap the role of the box by swapping the SD card out for a different one.  

Is this a limitation of Ubuntu or the eeepc?

Thanks

Chris

---

### Post by dabl on 2011-05-16
I have aptosid with Xfce desktop installed on a Eee PC 4G/701, for about two years now. I made the root partition 3.5G and left swap only about 350MB or so.  I don't think you can get Ubuntu onto 3GB, at least not for long.

Your card reader is actually a USB device, in BIOS.  So, if you want to boot a Linux off an SDHC card, which is possible (if not speedy), then you need to use the BIOS boot device setup to look first at the removable devices. I would format the SDHC card ext2, and set the /var/logs and /tmp to be tmpfs filesystems in /etc/fstab.  Let me know if you need more details.

---

