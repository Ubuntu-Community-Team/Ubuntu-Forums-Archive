---
title: "Monitor Resultion when Monitor NOT plugged in"
date: 2006-05-08
forum: Installation &amp; Upgrades
---

### Post by pkkid on 2006-05-08
I just installed ubuntu on my system and enabled Remote Desktop so that I do not need a monitor keyboard or mouse on this machine.  It is basically just a box sitting in the corner that I connect to thru Remote Desktop.

The resultion is fine when I boot the system up with the monitor connected.  I set the Resolution to 1280x1024.  However, when the monitor is unplugged and in the corner all that Remote Desktop can see is 640x480, which is entirly too small.

I did some searching in the /etc/X11/xorg.conf file to see if I could set something there, but it all seems fine to me.  There are refrences for all the standard resolutions upto 1280x1024 in all the categories.

Any ideas?

---

### Post by pkkid on 2006-05-08
Figured this out! :)

In my /etc/X11/xorg.conf file, I had this under "Monitor"

```
Section "Monitor"
	Identifier	"SDM-HX73"
	Option		"DPMS"
EndSection
```

I changed it to the below to manually define the Sync and Refresh Rates.  After a Reboot I was in 1280x1024 resolution with no monitor plugged in. :)

```
Section "Monitor"
	Identifier	"SDM-HX73"
	Option		"DPMS"
	HorizSync	30-100
        VertRefresh	50-150
EndSection
```

---

