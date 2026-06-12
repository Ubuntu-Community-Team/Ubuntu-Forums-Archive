---
title: "Installing Beryl (Dapper)"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by DuckFish on 2006-12-17
According to [the install page on the Beryl wiki](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/AiGLX), I'm supposed to have this in /etc/X11/xorg.conf:
```
Section "Module"
# Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dbe"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10&#8243;
Load "type1&#8243;
Load "vbe"
EndSection
```
This is what I have:
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```
GLcore and dbe are missing. What do I do?

I have an Integrated Intel video card (48MB, old computer).
Thanks :)

---

### Post by dbbolton on 2006-12-17
just add those lines, i guess

---

### Post by anubhavrocks on 2006-12-18
make a back up of your original xorg.conf before fiddling with it!use the xorg.conf as suggested on the Beryl site.

---

