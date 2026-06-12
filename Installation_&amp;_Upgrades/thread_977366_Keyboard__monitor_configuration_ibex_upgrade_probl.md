---
title: "Keyboard / monitor configuration ibex upgrade problem"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by smigg on 2008-11-10
I've recently upgraded from 8.04 to 8.10 and am having some issues related to my xorg.conf (or whatever setup has replaced this)

I have 2 monitors and an nvidia graphics card. After upgrade the monitor setup was fine, but the keyboard setup was screwed  - the insert/delete/home block and the arrow keys didn't work.

I tried reconfiguring my xorg config by running "sudo dpkg-reconfigure -phigh xserver-xorg". Now my keyboard setting are fine, but only one monitor works.

I thought Ibex would make this "just work". What should I do?

Thanks

my current xorg.conf:

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
EndSection

---

