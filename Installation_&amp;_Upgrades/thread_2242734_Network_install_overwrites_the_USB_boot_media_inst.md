---
title: "Network install overwrites the USB boot media instead of local hard drive"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by Jack_Eckman on 2014-09-03
Hello, I am trying to install Ubuntu 14.04 desktop to multiple systems via a local http server/mirror and usb boot media.  I have created a USB drive from the minimal iso and edited the txt.cfg to grab a preseed file from my local http server and to use this same server as the mirror.  When i boot the desktop from the USB and select install it gets the preseed file and is pulling the installation from my http server but its overwriting the USB drive instead of targeting the hard drive for install.  I am assuming that the usb is getting assigned /dev/sda1, is there a way to point/select the correct target drive for installation?  I had this working fine with Precise so i am not sure what i am missing.  Thanks for any guidance.

---

