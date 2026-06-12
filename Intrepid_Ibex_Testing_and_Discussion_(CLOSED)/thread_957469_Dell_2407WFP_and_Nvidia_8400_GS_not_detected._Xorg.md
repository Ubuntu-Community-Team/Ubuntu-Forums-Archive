---
title: "Dell 2407WFP and Nvidia 8400 GS not detected. Xorg in low res mode."
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tilapia on 2008-10-24
I've been using Intrepid for a week or two and have found in great. However, today, Xorg suddenly stopped working and my Dell 2407WFP display was defaulting to a resolution of just 1024x768, rather than the usual 1920x1200. I messed things up so have reinstalled, but still can't get the 1920x1200 resolution. 

This is all I have in my xorg.conf, which has been automatically generated.

[PHP]
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection[/PHP]

I've tried booting into rescue mode and using the xfix tool. This gets me a working X, but a very low res. I've also tried dpkg-reconfigure xserver-xorg (with both the -plow and -phigh settings). Every time I do this it gives me options to choose the keyboard and mouse settings but never detects either the graphics card or the display. 

I've tried installing the Nvidia driver, but get a black screen. 

Any ideas what else I can try, please?

---

### Post by tilapia on 2008-10-24
I am completely wrong! It does work correctly. The fault was caused by a new Belkin Switch2 KVM switch which is interfering with hardware detection. Obviously not as Linux-compatible as claimed...

---

