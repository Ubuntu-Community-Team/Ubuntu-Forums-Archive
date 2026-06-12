---
title: "Karmic, Android SDK, fastboot, ADB"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mperry on 2009-10-26
The default instructions for Jaunty for setting up the Android SDK and by extension using adb and fastboot seem a bit different for me now on Karmic RC. On Jaunty, I could simply add a udev rule like this:

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"

Add my path to the SDK tools to the .bashrc and source it and off I would go. This time getting this all going on Karmic requires a reboot. The android phone, my HTC Magic, would never show up in lsusb even after restarting the udev service, making it reread the usb "tree", etc. It did work on "root" but I don't want to do it that way. I want it on my user. So, after a reboot, the phone showed up and I could flash the recovery ROM and then upgrade my phone.

Perhaps a minor nit; but it is different and required a restart of my system. Anyone else finding this on karmic RC?

---

### Post by Martey on 2009-10-26
When I was configuring the SDK (just bought a HTC Hero!), I was not able to replicate this. Did you restart the udev service after adding in the new rule?

---

