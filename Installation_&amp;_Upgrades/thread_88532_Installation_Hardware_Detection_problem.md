---
title: "Installation Hardware Detection problem"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by CPU on 2005-11-10
Ok, I'm a bit new to this, a friend gave me a Hoary Hedgehog CD set to try out and I've had a few problems with with both of the installation and live CD on one of my computers (Runs beautifuly on the others)

Anyways, I stick in the live CD (or the Install CD, it doesn't matter) and it goes to the first screen, asks me if I wan't to advanced boot it, which I might add I've done dozens of times with different things, so I go and I hit fine, boot.  So it starts scrolling down detecting my hardware, but as it gets past the USB ports and right after it registers the mouse it seems to freeze, yet if I unplug and then replug something in while it's still running it will deregister and reregister the device so I know that it's still active in some form or another, but I still can't figure a way past that.

This is a little bit of what is onscreen before it freezes:

ata1: command 0xa0 timeout, stat 0xd0 host_stat 0x21
USB core: registered new driver hiddev
input: USB HID v1.10 mouse [microsoft microsoft 5-button mouse with IntelliEye(tmp) on usb-0000:00:1d.2-1
USB core: registered new driver usb HID
drivers/usb/input/hid-core.c: v2.0:USB Hid core driver
mice: PS/2 mouse device common for all mice

and following that it doesn't seem to do anything besides what I've already discribed.

Any suggestions/help would be greatly appreciated.

CPU

---

