---
title: "[SOLVED] No Edgy with Asus M2N-MX"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by siddartha on 2007-01-19
I just build up a system with an Asus motherboard (M2N-MX) and it doesn't want to start the CD. I mean it goes on for a few minutes than freezes before getting to the desktop. This board has a nforce430 and an onboard graphical interface geforce6100. I don't seem to find any problem related.

---

### Post by siddartha on 2007-01-28
The quick fix went like this: for nforce there is need of a 2.6.18 or newer kernel. As that wasn't in the Edgy repositories I moved up to Feisty with a 2.6.19 kernel. They say this 2.6.19 has some bug fixes with the nforce drivers so it's even better. I did all the setting I knew about it, installed nvidia-glx and everything worked like a charm. At least the lower level part (below the GUI/Desktop).

Some catches with the Edgy were - it recognised the Nvidia video card so it started the free nv x server. Wrong. 6100 seems to work with vesa. Next, everything is onboard - audio, networking... it couldn't recognise them - the device manager only showed the numbers for ID and no names. I inserted with modprobe the ethernet driver - dmesg will show the first line about the reverse engeneered driver and nothing more like the name eth0 or the hw address. Weird.

Feisty works like a charm. Knows about cool'n'quiet and scales the processor down and up as needed. The net card works and I haven't noticed any problems that aren't the fault of the net provider. The screen is crisp and the glx extensions work with no problem. Only the gnome interface is quite broken. So the interface went down several times but the console fixed everything and the system was back up.

The conclusion would be: no edgy but soon feisty.

---

