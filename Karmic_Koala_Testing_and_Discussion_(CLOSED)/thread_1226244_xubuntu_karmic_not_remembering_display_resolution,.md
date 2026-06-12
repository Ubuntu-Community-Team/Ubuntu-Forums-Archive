---
title: "xubuntu karmic not remembering display resolution, refresh rate"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Eeqmcsq on 2009-07-29
My install history is xubuntu 8.10, upgraded to 9.04, upgraded to 9.10 karmic development branch. Each time I log in, xubuntu uses the highest available display resolution and refresh rate, in my case, it's 1152x864@75Hz. I use Applications->Settings->Display to change to 1024x768@70Hz, and the screen changes correctly. But the next time I log in, xubuntu returns back to 1152x864@75Hz.

My video card is an integrated video chip. The computer itself is about 10-11 years old:
VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X (rev 5c)

My xorg.conf is pretty bare:
```
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
	DefaultDepth	16
EndSection

```

This was not a problem in 8.10. It was a problem in 9.04 and still is a problem in the karmic development branch. I'm curious if anyone else has seen this problem with xubuntu.

---

