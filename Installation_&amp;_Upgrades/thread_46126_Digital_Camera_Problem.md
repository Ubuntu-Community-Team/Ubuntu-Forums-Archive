---
title: "Digital Camera Problem"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by Ramon Lasa on 2005-07-03
How do I get Ubuntu Hoary Hedgehog 5.04 to recognise that I have plugged my Olympus 440 Digital Camera into the USB port?  Any help would be appreciated.

Ramon

---

### Post by coolclassic on 2005-07-03
What you need is the device serial number from your camera. Then you will have to edit the following file /etc/hotplug/usb/libgphot2.usermap
this holds all device serial numbers for most cameras but not yours.
To get this number you will need to use the command "udevinfo" for the full command try the man pages or someone on the forum might help here. Your camera should hopefully automount after this.

---

