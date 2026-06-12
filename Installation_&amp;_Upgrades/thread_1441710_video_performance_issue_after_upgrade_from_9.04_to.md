---
title: "video performance issue after upgrade from 9.04 to 9.10"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by elambert on 2010-03-29
After upgrading from Ubuntu 9.04 to Ubuntu 9.10, my Intel video driver is performing horribly slow. I had to switch to the vesa driver, but that one does not support the resolution of my monitor.
I now have all the latest packages installed according to the upgrade manager, but the problem remains.
My system is a DELL Optiplex 760. On Ubuntu 9.04 it was working very nicely. Below is my xorg.conf. I would very much appreciate a hint on how to solve this problem.
I checked [https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance) and indeed /dev/dri/card0 is missing : but there is no information on how to solve this ? :confused:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2944 1080
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by dstew on 2010-03-29
You might try reconfiguring X by the method described [here]("http://ubuntuforums.org/showthread.php?p=8302145#post8302145").

---

