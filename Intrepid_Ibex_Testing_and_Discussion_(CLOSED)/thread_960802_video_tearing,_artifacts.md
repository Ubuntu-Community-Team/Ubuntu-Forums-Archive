---
title: "video tearing, artifacts"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gedemins on 2008-10-27
don't know if its particularly intrepid problem, but here it is:
after installing new restricted video drivers from ati, i've been experiencing 
a) video tearing in vlc/totem in fast scenes of movies;
b) lots of artifacts when maximizing/resizing windows and video (when compiz is turned on), (see attachment for an ugly line)
c) when launching video, screen goes black first, and only then it launches. 
d) lots of pixels, that look like stuck, but appear on a screenshot too, so hope these are the artifacts too.

maybe something incorrect in my configuration? does anyone have these video card problems?

running ubuntu intrepid ibex x64 (latest updates)
radeon x1900xt
xorg.conf:

```
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
	Driver	"fglrx"
EndSection
```

---

