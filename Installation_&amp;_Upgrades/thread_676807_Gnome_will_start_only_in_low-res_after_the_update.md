---
title: "Gnome will start only in low-res after the update"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by JediKnight on 2008-01-24
I I have Gutsy, Radeon 9600, 2.6.22-14-generic kernel and tried to update the drivers

I followed this link [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) and did everything there (I followed both 'alternatives' since the first of them did not work perfectly (that means I installed the official proprietary 8.1 packet)

Now Gnome will start only in low-res mode

The effects (at least in this mode) will not work, and I can't select them

---

### Post by JediKnight on 2008-01-24
Partial resolve:

What I followed was this

> An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section

My file went that way

```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Screen	0
	Option		"MergedFB"	"off"
EndSection
```

Two "ati" strings... I changed them both to "fglrx" and then Gnome would start only in low-res mode. When I restored them, I can boot again in hi-res mode

BUT, everything is TOO slow whenever I resize, move windows or scroll

I also performed a fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

Segmentation fault (core dumped)
```

---

