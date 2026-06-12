---
title: "Ubunutu ARM, Beagle B5, no USB"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by dbc_too on 2011-03-02
If there is a more appropriate forum for this question, please direct me there.

I am trying to install 10.10 on a rev B5 Beagle Board following [OMAP Maverick Install]("https://wiki.ubuntu.com/ARM/OMAPMaverickInstall") and can not get the keyboard and mouse to be recognized. The system boots all the way to the "System Configuration" welcome screen, but without a mouse/keyboard I can't do anything. I suspect the hub is not getting recognized.

I have tried: two different powered USB 2.0 hubs, using a mini-A to mini-B USB cable. Tried two different mice. 

What should I try next to get USB to wake up?

Can someone please clarify how to enable console messages on the serial console?  It's pretty annoying to have *all* the information needed to debug the problem totally hidden.  The instructions on the above mentioned wiki page are not clear about where to find the image that I need to dd off of the SD card and modify to enable the serial console.

-dave

Additional information:
Ohm meter confirms usb cable shorts pins 4 & 5
USB connector pin 1 is never driven with 5V, indicating that the port never goes over to host mode.

---

