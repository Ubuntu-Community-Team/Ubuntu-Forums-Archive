---
title: "Did I beat the nVidia-96 problem?"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2011-05-01
I was about to put out a call for professional help in solving the video problems that came along with the upgrade from 10.10 to 11.04, when something happened (earlier I had been getting too much work IRQ 16) after I reinstalled 11.04 for a third time (over previous install), a second proprietary graphics driver was listed (accelerated nVidia) and I tried to make it work.  It didn't, and I had to go to failsafe graphics mode which came up as 1280 x 1024 at 0 Hz.  I rebooted only to find myself back with 1024 x 768 at 60 Hz with a mispositioned cursor.  I then went into root and saved xorg.conf.failsafe as xorg.conf .  This is what I am using:

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

Furthermore, this appears to work with users I am adding while before user logons gave garbled graphics.

What am I doing right or wrong?  How can I make it better?

John

---

