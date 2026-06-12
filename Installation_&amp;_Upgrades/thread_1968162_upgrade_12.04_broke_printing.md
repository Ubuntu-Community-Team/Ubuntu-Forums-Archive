---
title: "upgrade 12.04 broke printing"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2012-04-28
Upgraded to 12.04 and lost my printing capability.  The lp... commands say that the printer is there and that it is ready to receive print jobs, but when I try to print something it gets stuck in the print queue and will not print.

---

### Post by arvevans on 2012-04-28
Apr 28 21:47:02 arv-desktop kernel: [29022.539112] usblp0: removed
Apr 28 21:47:04 arv-desktop kernel: [29024.554234] usblp0: USB Bidirectional printer dev 11 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0838
Apr 28 21:47:04 arv-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2.5/3-2.5:1.1/usb/lp0
Apr 28 21:47:04 arv-desktop udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2.5
Apr 28 21:47:04 arv-desktop udev-configure-printer: Device already handled

It still doesn't print.    :confused:

---

### Post by dino99 on 2012-04-29
seems that usb3 is used, should be the problem

---

### Post by arvevans on 2012-05-16
FIXED!  I had to find, download again, and re-install the Epson drivers for this all-in-one printer.

Seems that the 12.04 release broke a whole bunch of previously working things.  I have had to re-install several of my own software programs they became "disconnected" in the process of upgrading to 12.04 Ubuntu.

Also, I had relied strongly on the web page editor part of seamonkey but the upgrade totally removed seamonkey from my system. 

It seems that with the 12.04 upgrade we are now faced with an attitude at Ubuntu which says "**we should only use Ubuntu applications...and be satisfied with that**"  This has the look and feel of Microsoft approach over the past years.  Apparently when a software company gets big, it also gets dictatorial.

---

### Post by Skaperen on 2012-05-17
> **arvevans said:**
> It seems that with the 12.04 upgrade we are now faced with an attitude at Ubuntu which says "**we should only use Ubuntu applications...and be satisfied with that**"  This has the look and feel of Microsoft approach over the past years.  Apparently when a software company gets big, it also gets dictatorial.
I don't see that happening (and I tend to be a sharp critic at times).  More likely it is a case that they just don't have that custom or alternate software to do regression testing with.

---

