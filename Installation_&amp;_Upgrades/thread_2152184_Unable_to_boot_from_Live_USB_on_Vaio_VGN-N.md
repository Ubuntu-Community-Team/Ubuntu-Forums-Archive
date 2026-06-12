---
title: "Unable to boot from Live USB on Vaio VGN-N"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by M3m3nt0 on 2013-06-07
Hi everybody!

I'm trying to test Ubuntu 13.04 on a friend's Vaio VGN-N actually equipped with Windows 7.
I've two different USB sticks that I used successufully different times on different laptops/desktops to boot with Ubuntu 13.04; on this Vaio both of them simply doesn't work!:o

Maybe I'm doing something wrong...

I've enabled the boot from external devices in the BIOS and set the USB as first device (and the HDD as last...)

Any suggestion?

---

### Post by vadimkolchev on 2013-06-07
Please, give some more facts. What exactly does that mean - it doesn't work? Despite of USB inserted your Vaio boots straight to HDD and not USB? If yes, try to burn your image once again to USB using ImageWriter, if you have existing windows installation or dd if you have linux installation.

---

### Post by M3m3nt0 on 2013-06-20
> **vadimkolchev said:**
> Please, give some more facts. What exactly does that mean - it doesn't work? Despite of USB inserted your Vaio boots straight to HDD and not USB? If yes, try to burn your image once again to USB using ImageWriter, if you have existing windows installation or dd if you have linux installation.

Sorry for the lack of informations...
Yes, as you wrote, despite of USB inserted the laptop boots straight to HDD and not USB.

But I've found the solution!! :D

The exact model is Sony Vaio VGN-N21M/W [SIZE=1](to help in future search ;))[/SIZE]

I enabled the option *External Drive Boot* under ***Advanced*** tab in the BIOS settings; then under ***Boot*** tab I've set the USB as first device to boot and _excluded_ the HDD from the list (by pressing X ). Without excluding the HDD the USB won't boot!

Hope this helps others with USB booting problems!!



Solved for me: I've to change the topic title by inserting [SOLVED] (or other tags)?

---

### Post by sudodus on 2013-06-20
I'm glad you are sharing your solution :-)

Edit your first post, go advanced and change the prefix to SOLVED.

---

### Post by djps on 2014-04-04
Thank you so much for this! I was giving up with the same problem. My laptop is an older Sony: VGN-C2Z model and same issue in bios.

---

