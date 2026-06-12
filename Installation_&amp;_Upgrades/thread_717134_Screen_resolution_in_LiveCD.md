---
title: "Screen resolution in LiveCD"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by ccprog on 2008-03-06
This post is not so much a question, but to share a weird experience. Maybe someone can even make sense out of it. 

I have spent the last few days configuring a custom Live CD from Ubuntu 7.10. My initial experience was that during the LiveCD was runing I was not able to change the screen resolution. I then started to experiment.

My system has a NVidia GeForce4 MX 440 graphics card and a Samtron 7Ei CRT display. All variants were run with the free nv driver that is shiped with the LiveCD. The xorg.conf written during session setup had this to say about screen properties:
```
Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

[LIST=1]
[*]**Out of the box**
[LIST]
[*]gnome started with 1280x1024@60Hz
[*]gnome-display-properties was not able to change the screen resolution
[*]trying to use gtk-displayproperties resulted in dropping to an X screen
[/LIST]
.
[*]**Setting boot options:** I tried to set vga=791, vga=792, from the F4 dropdown list 1024x786 16 and 1024x786 32 (depth 24 wasn't offered)
[LIST]
[*]The result was the same as before.
[/LIST]
.
[*]**Altering gconf:** I added the following keys to /etc/gconf/gconf.xml.defaults/%gconf-tree.xml:
```
key=/desktop/gnome/screen/default/0/rate value="85"
key=/desktop/gnome/screen/default/0/resolution value="1024x768"
```
[LIST]
[*]The result was the same as before.
[/LIST]
.
[*]**Both:** With the altered gconf defaults, I set boot options vga=792, from the F4 dropdown list 1024x786 16 and 1024x786 32
[LIST]
[*]Same result.
[/LIST]
.
[*]But then suddenly, when setting boot option vga=791(still with gconf defaults set)
[LIST]
[*]gnome started with 1024x786@85Hz
[*]gnome-display-properties was perfectly able to change the screen resolution
[*]trying to use gtk-displayproperties still resulted in dropping to an X screen
[/LIST]
[/LIST]
.
The most amazing thing to lern was that, contrary to what I read in several places, setting the screen resolution as a boot option did have, under certain circumstances, an influence on the behavior of the X server. Incidentally, in none of the above cases did the gfxboot splash screen change its resolution. It always remained at 640x480.

---

