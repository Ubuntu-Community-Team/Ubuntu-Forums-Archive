---
title: "edgy nvidia fiasco and recovery"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2006-10-27
Ubuntu 6.10 + NVIDIA

After installing the nvidia driver package (nvidia-glx) and following the instructions in the package ("sudo nvidia-glx-config enable"), my X11 server was trashed and only the console was working. 

After fumbling around for an hour or two I discovered a simple solution: do not run nvidia-glx-config at all, just modify the original  /etc/X11/xorg.conf  file to change the driver from "nv" to "nvidia" and add the desired screen resolution:

Section "Device"
...
    Driver        "nvidia"

Section "Screen"
...
    SubSection "Display"
        Depth        24
        Modes        "1920x1200" "1600x1024" "1280x1024" "1024x768" 

This is what worked for me, but no guarantees. 

I have enjoyed this Nvidia-X11 disaster several times with Ubuntu (of course it is my problem, not theirs).

I have also done this Nvidia driver task several times with Fedora, and never had a failure. Ubuntu, please clean up your act.

---

### Post by OlineSixtyOne on 2006-10-28
I encountered the same problem. After I ran ("sudo nvidia-glx-config enable"), I looked at xorg.conf and discovered that the BusID for my graphics card was wrong. 

I changed this:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection
```
to this:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection
```

After that all is well. You'd be better off not running ("sudo nvidia-glx-config enable") in the first place though.

---

