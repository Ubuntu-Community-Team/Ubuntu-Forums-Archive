---
title: "Intrepid Resolution i845"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by 3amConspiracy on 2008-10-31
My monitor is stuck at 640x480 resolution. I have an i845 chip. I got it to work under Hardy by changing xorg.conf I tried doing the same in Intrepid but it doesnt work. At one point I got it to kind of work but then it just hung at the brown screen after I logged in. I tried using screen resolution but it won't even auto-detect my display.

:edit: here is what my xorg.conf file says:
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by 3amConspiracy on 2008-10-31
Okay I figured it out. After more searching and getting some sleep.

I had to just manually download the drivers then convert the .rpm file to .deb

Intrepid is pretty fast compared yo hardy I love it!!!:guitar:

---

### Post by Yan_Suryana on 2009-01-11
> **3amConspiracy said:**
> Okay I figured it out. After more searching and getting some sleep.

I had to just manually download the drivers then convert the .rpm file to .deb

Intrepid is pretty fast compared yo hardy I love it!!!:guitar:

Hello,

I use a mainboard with an onboard i845 chip. Install 8.04 was ok, but I can't install 8.10 and just got a Blank Screen with a Mouse Cursor.
How can I figure it out ?
Please Help.

I am new in Linux.
Thanks ..

---

