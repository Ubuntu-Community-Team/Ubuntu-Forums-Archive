---
title: "[SOLVED] usb printer not detected"
date: 2008-07-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scradock on 2008-07-09
I am testing Intrepid on the same laptop that I run 8.04 on. I added an old laser printer, connected through a USB cable. Hardy detects it flawlessly and lists its URI as "usb://HP/LaserJet 1100".

Intrepid does not autodetect it; when I go to System | Administration | Printers and try to Add a New Printer it does not detect the connected printer, and if I add it manually with the same URI as above it remains unconnected; Test pages don't print, and it isn't available in Print dialogs.

I noticed that system-config-printer has been updated from 0.7.81 to 1.1git. Does anyone know if this is a known deficiency that will soon be fixed, or is there a workaround?

Thanks in advance - Intrepid is working very well otherwise, and I would love to fix this!

BTW, my network printer autodetected perfectly! Maybe there is something lacking in the usb sub-system?

---

### Post by olskar on 2008-07-09
I heard something about they were making Ubuntu download printer drivers from the internet in intrepid, could it have something to do with this?

---

### Post by scradock on 2008-07-09
> **olskar said:**
> I heard something about they were making Ubuntu download printer drivers from the internet in intrepid, could it have something to do with this?

The printer driver database came up as usual when I specified the make and model of the printer in the manual attempt to install, so I don't think its a problem in that area.

I looked in System | Administration for the hal front-end, to see if there was any information about the usb subsystem, but it's not there. I had heard there were changes in hardware detection, but it seems we are stranded without any front-end at the moment.

Synaptic reports that hal is installed, and there is a package hal-cups-utils that should be browsing local printers through hal. Maybe that's what isn't working?

---

### Post by scradock on 2008-07-09
Sorry about that, everyone. It seems that the USB-parallel port connector had died, sometime after I set up the printer under 8.04, but before I tried to use it under Intrepid. When I checked again, it didn't work under either Intrepid OR 8.04 (or WinXP for that matter).

If anyone is interested, I had to connect the printer and connector to a Vista machine, which diagnosed a fault in the connector/driver. Ubuntu just swore blind there was no printer there; XP saw an unknown USB device but couldn't talk to it. All consistent with a dead converter chip, CH341, from a Chinese manufacturer who gives out driver files but no instructions in English.

---

### Post by cariboo on 2008-07-09
I'm sure if you checked the output of dmesg you would have seen something similar.

JIm

---

### Post by scradock on 2008-07-09
> **cariboo907 said:**
> I'm sure if you checked the output of dmesg you would have seen something similar.

JIm

Thanks Jim - good suggestion. dmesg does mention the ch341-uart as an USB device, but only when it FAILS to connect through. There is no info about what the heck ch341-uart is or is supposed to do.

Now I have it working again(!) and dmesg doesn't even mention the ch341, just goes straight to registering the printer.

---

