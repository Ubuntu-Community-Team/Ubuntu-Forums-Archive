---
title: "Mini Install to Aspire One ZG5, Home on SD card"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by firedrow on 2010-11-30
I'm using the mini.iso to install Ubuntu 10.10 on my Acer Aspire ZG5 netbook.  During the install it only saw the internal 8GB SSD, so I installed the whole OS on that.  After the install I was able to fdisk and format the SD card in the left hand slot and mount it.  But after I added the mount to /etc/fstab when I rebooted I get the purple Ubuntu 10.10 screen saying:

> The disk drive for /media/SDhome is not ready yet or not present

Continue to wait; or Press S to skip mounting or M for manual recovery

I have to skip or wait while it does nothing.  When I get back to console I can mount the drive just as I need it.  So what am I missing?  I assume the SD driver isn't being loaded soon enough.

---

