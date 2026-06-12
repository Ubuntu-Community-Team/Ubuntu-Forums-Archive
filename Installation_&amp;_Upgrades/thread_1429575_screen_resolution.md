---
title: "screen resolution"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by srikrishnan on 2010-03-14
Hi All,

I have installed Ubuntu 9.10 as a second OS in my System. The maximum available screen resolution is only 600. I am not able to change it. But in my XP OS i set it as 1024X768.

My System Configuration is as follows:

Monitor: 17inches Samsung Syncmaster 753s
Motherboard: ASUS M2N 68 CM
Processor: AMD ATHLON(tm) 7750 Dual Core 2.70Ghz
Ram: 1 GB

Here I have pasted my xorg.conf file details:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Please anybody help me to solve this problem

Thanks,
Srikrishnan

---

### Post by zeroseven0183 on 2010-03-14
Hi!

Is there anything to install in Hardware Drivers from System > Administration?

---

### Post by srikrishnan on 2010-03-15
Hi,

Thanks for your reply.

your mail give me a flash, to check the Nvidia accelerator driver. First I installed Version 175 now i changed it to version 185 which is recommended. Now my problem solved. 

Again Thanks for your guidance.

Thanks,
Srikrishnan

---

