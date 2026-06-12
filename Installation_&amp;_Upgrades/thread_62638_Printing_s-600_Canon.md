---
title: "Printing s-600 Canon"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by clsnyder on 2005-09-05
Hi -
new to linux/ubuntu
newly installed Hoary 5.04 
seemed to install printer driver OK (is there a way to verify that it was installed?)

printer is on usb port - computer can't seeem to find it (no response to test page), even when I go to properties/connection in the GUI and select USB Printer #1 (Canon S600) - which is listed. 

? Help

TIA

---

### Post by robins_web on 2005-09-06
[QUOTE=clsnyder]Hi -
new to linux/ubuntu
newly installed Hoary 5.04 
seemed to install printer driver OK (is there a way to verify that it was installed?)

printer is on usb port - computer can't seeem to find it (no response to test page), even when I go to properties/connection in the GUI and select USB Printer #1 (Canon S600) - which is listed. 

? Help

TIA[/QUOTE]

I had the same problem with my Canon S300. A couple of ideas: make sure your /etc/modules has these lines:
lp
usbcore

Add yourself to the lp group, then reboot. Be sure the printer is connected and turned on when you reboot!

Try [http://www.linuxprinting.org](http://www.linuxprinting.org)

Finally, a Very Wise Person told me "Linux + Canonv = Not Good. Linux + HP =  Good."

So I broke down and bought an HP PSC 1310 All-In-One for less than $65 at Sam's Club. Works like a charm.

At $65, how can you go wrong? What's your time worth?

Robin

---

### Post by rafakl on 2005-09-06
I have an USB printer attached and works very well!!!

But it isnt a Cannon, is an HP DeskJet using the drivers that came with Ubuntu, not need to download anything.

---

