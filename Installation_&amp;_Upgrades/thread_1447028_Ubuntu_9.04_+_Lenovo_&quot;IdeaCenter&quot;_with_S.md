---
title: "Ubuntu 9.04 + Lenovo &quot;IdeaCenter&quot; with SiS 307DV graphics"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by usrerco on 2010-04-04
I found the default install of Ubuntu 9.04 on my Lenovo "IdeaCenter" desktop would only come up in low res graphics modes (eg. 800x600).

The only choices in System > Preferences > Display was 800x600, and I think 640x480, either of which makes the window manager very limited.

The Display program seemed unable to detect the monitor correctly, and thus only offered limited resolutions.

At first I thought it was a graphics driver issue, and spent hours with that, all in vain.

In the end, I found the /etc/X11/xorg.conf file just needed a little tweak in the "monitor" section (first saved a copy of my working lores xorg.conf file!), and just added these lines to the 'Section "Monitor"':

	HorizSync    30.0 - 60.0
	VertRefresh  50.0 - 160.0

So for example, before the change, it read:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

```

..and after the change, it read:
```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync    30.0 - 60.0
	VertRefresh  50.0 - 160.0
EndSection
```

With those changes, I found I could choose better display resolutions, which made the machine usable.

You can crank the max values in those sync lines higher to get higher resolutions (e.g. 60.0 -> 70.0, and 160.0 -> 170.0) Just watch you don't set it to high; some old CRT monitors can literally fry with the wrong settings.

I found it was useful to test my changes to the xorg.conf file quickly by restarting the window manager with ALT + PRINTSCREEN + K (ALT has to be the right hand ALT key). This totally *kills* the window manager (closes your windows!) and restarts it, so that it re-parses your changed xorg.conf. This is apparently ubuntu's equivalent key sequence for the older CTRL-ALT-BACKSPACE, which seems to no longer work.

I also found (CTRL) + (ALT) + (PLUS) was useful to cycle through the various screen resolutions. (The (PLUS) being the plus key on the numeric keypad) During testing I sometimes found the OS would pick a resolution too high for my monitor and it would go black.. but typing CTRL-ALT-PLUS while the black screen was up would let me cycle to lower screen resolutions until I found one the monitor likes, then later fix things correctly using  System>Prefs>Display settings, and lowering the max sync ranges in the xorg.conf.

Hope that helps..

---

