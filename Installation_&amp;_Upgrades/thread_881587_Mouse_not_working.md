---
title: "Mouse not working"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by BiscuitTin on 2008-08-06
After some difficulty I've managed to get Ubuntu 8.04 installed and the dispay working. The problem I currently have is that the mouse is not working. The mouse is built into the keyboard and is one of those laptop style pads. The keyboard works fine.

As far as I can determine:

/dev/mouse refers to /dev/input/mice

In the "Mouse0" section xorg.conf refers to /dev/input/mice and uses the driver "mouse".

Under /dev/input/by-id I get two mouse entries called:

usb-Sony_RF_Receiver-mouse
usb-Sony_RF_Receiver-event-mouse

So it looks like my device is identified by the system, but how do I determine whether it works correctly and what device it is actually mapped to?

---

### Post by BiscuitTin on 2008-08-06
Ok, I've found that my mouse device is registered on /dev/usb/hiddev1. When I do a cat /dev/usb/hiddev1, I get responses to mouse clicks and movement on the touchpad. The thing is that this doesn't happen when I can /dev/input/mice or /dev/input/mouse1. I get responses to the buttons but not the mouse movement. It would appear then, that the device is not properly bound to /dev/usb/hiddev1.

How does one check this and how does one map the devices correctly?

---

### Post by wpshooter on 2008-08-06
Have you looked into the BIOS settings regarding mice devices and see that they are all set properly.  You might have to disable other mice types in order for your keyboard related mouse to work properly.

---

### Post by BiscuitTin on 2008-08-06
Can't see any specific options for the mouse in the BIOS. Its very basic compared to most modern BIOSes. Anyway, I found and plugged in a standard USB mouse and this works fine. Really need the pad on the wireless RF keyboard to work though.

---

