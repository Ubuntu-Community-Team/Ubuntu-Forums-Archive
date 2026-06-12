---
title: "tv time is not working."
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kseise on 2008-09-07
```
$tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/kseise/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
```

Anybody know how to fix this?  I am running 8.10 Alpha 5 on AMD 64 with an nvidia card.

---

### Post by olskar on 2008-09-07
what s the output from xvinfo?

---

### Post by beartard on 2008-09-07
And which drivers do you use for your nvidia card?  The proprietary nvidia binaries do work for tvtime on amd64.

---

### Post by kseise on 2008-09-07
> xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present


I am using the nvidia driver I believe.  When I just went to double check (Hardware Drivers), there is a box saying "In Use" and another that says "Enabled".  Only the In Use box was checked.  Now I need to reboot to see if the "Enabled" box makes a difference.

---

### Post by kseise on 2008-09-07
It made all the difference in the world.  Thank you.  It works fine now.  I don't understand how the driver could be In Use, but not Enabled.

---

### Post by Nullack on 2008-09-08
Before we all forget about this - what driver were you running before installing the nvidia one? Were you using the nv driver?

Does the nv driver not work with tvtime?

My thinking here is if we isolate the root cause and summarise it in a bug report that will help the devs move on fixing it.

---

### Post by RAOF on 2008-09-08
> **Nullack said:**
> Before we all forget about this - what driver were you running before installing the nvidia one? Were you using the nv driver?

Does the nv driver not work with tvtime?

My thinking here is if we isolate the root cause and summarise it in a bug report that will help the devs move on fixing it.

The nv driver doesn't (or didn't, I'm not sure what exactly applies here) support XVideo acceleration.  A wishlist bug is unlikely to be particularly useful to anyone.  The nv driver kinda sucks :(.  Which is why nouveau exists.

---

### Post by Nullack on 2008-09-08
Thanks Chris, I now understand its not an existing feature of the nv driver and not a bug.

---

### Post by kseise on 2008-09-08
Here is a copy of the old xorg.conf video card section

> Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	0
EndSection

Looks like vesa not nv was having the problem.

---

### Post by RAOF on 2008-09-09
Heh.  VESA has *no* acceleration, let alone Xv :).

---

