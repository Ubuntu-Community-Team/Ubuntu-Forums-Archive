---
title: "install on usb with all updates"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by z0rr099 on 2013-08-25
I know I can easily install ubuntu on a usb stick from an iso image with unetbootin, etc, but how do I install it with all the updates since release of iso?
My thoughts are to actually do an install onto the usb stick, or install it on a computer (VM), make an iso using remastersys, then install on usb stick.
Any suggestions or help would be greatly appreciated.

---

### Post by sudodus on 2013-08-27
One way is to use an image and 'flash it' to the USB drive according like in the following link
[URL="https://help.ubuntu.com/community/InstalledSystemFakePAE"]
https://help.ubuntu.com/community/InstalledSystemFakePAE[/URL]

Another method is to simply perform the installation as usual, but to a USB drive instead of an internal drive.

The drives are 'mass storage devices' and treated in the same way by Ubuntu. This way you will be able to upgrade the kernel as well, and it will be more stable than a persistent live system (as made with Unetbootin).

If you want the system to be portable (work on many computers), you should avoid installing proprietary drivers, for example for graphics or wifi.

But an installed system as well as a persistent live system will be much slower than a normal live system, if the USB drive is slow. See this link

[URL="https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites"]https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites
[/URL]

---

