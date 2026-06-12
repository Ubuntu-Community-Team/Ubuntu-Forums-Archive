---
title: "Changes to USB install files"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by N6SXR on 2012-09-19
I have been trying to get my Dell b43 wireless device up and running.  Been a LONG time since I played with Linux/Unix.  Anyway, I have tried to follow a lot of the great help concerning installing the b43 legacy drivers and getting the wireless device up and running.  One thing I noticed was that after installing files specified, and they were there after the install, that after a reboot, as suggested, they are gone.  I currently have the install on a USB thumb drive and am wondering if I need to do the install to disk to get this working properly.  I am using 12.04.1.  I did try the software update as suggested but it gave some errors so I am wondering if this is an issue with the thumbdrive.  I did not see any activity to the drive.

I am thinking it is not possible to do these updates while running from the USB drive.

Any help is appreciated.

Kirk - N6SXR

---

### Post by windscape on 2012-09-19
Hi,

For files to persist after a reboot when using a Live USB drive, you need to create a persistence partition. The details for doing this vary depending on the utility used to get the image onto the USB drive. I used usb-creator from another Linux distribution that I moved from to Xubuntu to create a persistence partition. I'm not sure if there is a utility that can do the same on Windows.

Edit #1
If you have a second USB drive, you could use usb-creator in Ubuntu to create another Ubuntu Live USB drive with a persistence partition.

---

### Post by N6SXR on 2012-09-19
Thanks!  That does explain a lot.  Not that I fully understand it quite yet but it does help.  I bit the bullet and went ahead and made a dual boot system on my laptop.  I only really use it for my ham radio stuff so it is not super critical.  I suspect I will have better luck doing it this way.

Thanks again.

kirk - N6SXR

---

