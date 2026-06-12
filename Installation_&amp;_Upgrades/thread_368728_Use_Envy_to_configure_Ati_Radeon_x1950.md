---
title: "Use Envy to configure Ati Radeon x1950"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by revoltism on 2007-02-23
Hi,

Envy is a fenomenal script to help install the latest Ati or Nvidia drivers. I my case I used the manual install but got in to trouble.

If you don't heard of Envy. Get it here [http://www.albertomilone.com/index.html]("http://www.albertomilone.com/index.html")

I use an LCD screen and I don't know why but it got out of sync. In other word the resolution was not correct to support my screen. It was pretty easy to fix but could be hard for a newbe to figure out. Why i post this.

In /etc/X11/xorg.conf you have a section "screen" witch tells..

Use "sudo gedit  /etc/X11/xorg.conf" (gnome) or "sudo nano  /etc/X11/xorg.conf (safe graphic console)" 
```
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```


just change it to the one below

```
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection
```

Hope it helps =)

---

### Post by cortsenc on 2007-02-24
Yes, Envy is great!!

It configure my ATI Radeon 9600 perfectily!

---

