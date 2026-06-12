---
title: "lirc_mceusb2 causes suspend/resume to fail"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by wgandhi on 2008-04-26
I have installed Hardy heron on Intel Core2 Duo, 975XBX with NVIDIA 7300GS graphics and Haupagge HVR 1180 card. I use mythtv for PVR functionality. System works quite well for PVR but I cannot get resume to work if I keep the lirc_usbmce2 module loaded.  Problem is that it is the module of the remote so without it my machine does not wake on usb using the remote.

To unload the lirc I put the lirc_usbmce2 in the /etc/pm/config.d/ modules file with SUSPEND_MODULES="lirc_usbmce2"

I have to move the mouse everytime to get the machine going, its not too bad but would rather that this worked through the remote. Any suggestions would help..

-Wish

---

