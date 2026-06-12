---
title: "USB Keyboard and Mouse not working during installation"
date: 2013-07-09
forum: Installation &amp; Upgrades
---

### Post by some guy named dave on 2013-07-09
Hello. I'm trying to dual boot windows 7 and Kubuntu 13.04. However, after the booting process, once I get to the screen where it asks me if I want to try kubuntu or install it, my keyboard and mouse stop working. They work just fine in the bios and my Windows 7 install.


I've tried kubuntu 12.04 and 13.04, both amd64. I have also tried reconnecting both keyboard and mouse, but it didn't work. Once the installer opens up, they lights on my kb and mouse turn off and they stop working.










I'm rather new to linux and dual booting, so any help would be greatly appreciated. Thanks.


#edit: Here's my pc hardware.
Keyboard: 
Logitech G110 Black USB Wired LED Backlighting Gaming Keyboard

Mouse: 
Logitech G9x Black Two modes scroll USB Wired Laser 5700 dpi Gaming Mouse

Motherboard:
GIGABYTE GA-970A-UD3 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD Motherboard

Processor:
AMD Phenom II x4 955 @ 3.2 GHz

Video card:
SAPPHIRE Vapor-X 100358VXL Radeon HD 7770 GHz Edition 1GB 128-bit GDDR5 PCI Express 3.0 x16 HDCP Ready CrossFireX Support Video Card

RAM:
G.SKILL Ripjaws Series (4 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model F3-12800CL9D-4GBRL
.

---

### Post by some guy named dave on 2013-07-10
I've tried everything I can think of, and I've been googling this for hours and haven't found anything helpful. Any suggestions on this before I give up?

---

### Post by bokgeneraal on 2013-07-10
Maybe try the install with a standard mouse and keyboard? These things happen in the FOSS world because manufacturers don't often design for FOSS compatibility.

---

### Post by some guy named dave on 2013-07-19
I tried $10 logitech keyboard & mouse (USB) - nothing fancy, same result. They aren't detected or something. A ps/2 keyboard works, thought this motherboard only has one ps/2 slot. And using a ps/2 doesn't solve the USB problem.


Any other ideas?

---

### Post by wasia on 2013-08-19
In case of Gigabyte 970A-UD3, the "magic" BIOS option is "IOMMU Controller". Set it to "Enabled" and your keyboard will work (didn't tried mouse yet).
Good luck!

---

### Post by some guy named dave on 2013-09-11
Hey all, sorry for late response, have been busy with real life stuff.


In any case, after enabling IOMMU in my bios, I just copied the Kubuntu ISO on to a live usb and booted it, and my mouse and keyboard seem to work fine. Thanks for the help!

---

