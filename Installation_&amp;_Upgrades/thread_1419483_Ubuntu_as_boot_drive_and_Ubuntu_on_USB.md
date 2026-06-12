---
title: "Ubuntu as boot drive and Ubuntu on USB"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2010-03-01
I have Karmic as my boot drive on a 400 gig SATA disk. I have an old 320 gig PATA with Karmic on it, too. When I booted to the SATA, per usual today, and then turned on the USB drive with the "old" Karmic on it, the USB drive light flashed and flashed, but the SATA drive/OS could not "see" the USB drive.

Evem in GParted Live-cd, the 320 PATA drive could not bee seen. 

The PATA drive's jumper is (probably) set as Master. Does that matter?

All I want to so is re-partition the PATA on the USB for some storage for Linux and about 100 gig for Win7.

---

### Post by darkod on 2010-03-02
Have you connected it like that before? Does it have enough power on one usb cable if you don't have separate power cable?

---

### Post by Mark_in_Hollywood on 2010-03-02
This USB external hard disk drive enclosure has it's own power source. It is a USB 2.0 device. 

I have place a jumper to set the drive as "cable select", and powered the device up, but the indicator LED only flashes.

By the bye, it doesn't work under Karmic or Win7 (64 bit).

---

### Post by darkod on 2010-03-02
It all depends on the enclosure. Do you have a manual by the way? Also you might try without any jumper.

Otherwise, when using it like this the disk becomes USB from PATA and master/slave jumpers shouldn't matter at all. But it also depends how the enclosure is designed.

---

### Post by Mark_in_Hollywood on 2010-03-04
The 80 wire cable had a wire break. The device had to be replaced.

---

