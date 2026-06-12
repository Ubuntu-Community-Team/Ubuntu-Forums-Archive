---
title: "Don't Use Framebuffer"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by stoneheart on 2010-02-12
My monitor recent died and I'm using an old CRT as a replacement for now.  I get an error when Ubuntu starts saying it could not find a framebuffer compatible device.  It then gives me the option to boot into low res mode which I accept.  Once I login, the display actually looks fine, but I would like to get rid of the error message.

Anyone know how to remove framebuffer usage from the bootup process?  A text display is fine.  I looked in my xorg.conf, but I didn't find anything that I could tinker with.

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
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

### Post by Jose Catre-Vandis on 2010-02-12
> **stoneheart said:**
> 

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"  <<<
EndSection

EndSection

Change "true" <<< to false :D

(FB - framebuffer)

---

### Post by stoneheart on 2010-02-12
Thanks, Jose!  I'll try it when I get home.

---

