---
title: "[SOLVED] How can I make udev create /dev/usb/lp0 for my printer?"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by Norber_OK on 2008-10-06
I have an usb printer plugged in but I have no /dev/usb/lp0
I turn off the printer, then turn it on and no /dev/usb/lp0 is created.

Is it udev not working?
Is that udev is not detecting the printer?
Is there any log to see it?
What is happening?

I can create /dev/usb/lp0 by the terminal command:

sudo mknod /dev/usb/lp0 c 180 0

But it dissapear at reboot. And in the /dev/usb/ directory only appears:

hiddev0  hiddev1


Can I make udev create /dev/usb/lp0 for my printer in a way it persists at reboot?
Is there a way to communicate with the printer by knowing vendorID and productID or knowing other data?
Is this an udev issue or a kernel module issue or what?

I can not use my printer and I don't even know if my system is detecting it.
I am completely lost.
Any idea will be very appreciate.
Thanks in advance.

---

### Post by upchucky on 2008-10-06
mine only works if i have it physically plugged into the second usb connector, it seems that my bios will only allow a printer on this port.

---

### Post by Norber_OK on 2008-10-08
Thank you very much and sorry for my delay.
I tried to plugg-in my printer in each usb port of my pc and I found something very strange: The system only detects it when I connect it to my keyboard (my keyboard has two usb ports) then and only then it shows automatically a /dev/usb/lp0 device and then and only then shows it in a line when lsusb from terminal.
Then I have spent a day trying to configure it to work with cups but I'm getting "rastertogutenprint.5.2 error ..." message.
I think that now I have to generate a PPD file with gutenprint.5.2 beta 4

Any idea?

---

### Post by Norber_OK on 2008-11-03
I re-installed ubuntu hardy and then it automatically detected my Epson Stylus DX7000F printer on /dev/usb/lp0 (plugged in one of my keyboard's usb ports).

localhost:631 -> printers shows the driver:

Epson Stylus DX4800 - CUPS+Gutenprint v5.0.2 Simplified

It works OK
It is solved.
:p :p :p

---

