---
title: "Two monitors, Intel onboard graphics, Xubuntu Jaunty"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tgoose on 2009-03-21
Hello,

I upgraded one of my computers from Xubuntu Intrepid to whatever the current alpha of Jaunty is.  For Intrepid I had a SubSubSection in xorg.conf giving a virtual resolution so that I could use xrandr to set both monitors.

However:

now, if I have that SubSubSection in then the X server won't start at all, regardless of how many monitors attached.

If I comment out the SubSubSection then I can boot up with one monitor but if the second is attached then again the X server won't start.

If, having booted up with one monitor I then plug the other one in and try and set up xrandr I run into the problem of not having a large enough virtual resolution (because it's not set).

So, my question:

Is this broken because of the fixes I had to apply to Intrepid to get stuff working,

or is it broken generally at the minute?

More specifically, if I just wait is this likely to start working or do I need to undo some change that I've made to settings?


I ask mainly because of the deprecation of xorg.conf which (and I'm guessing here) could mean I should be setting a virtual resolution in some other way now instead of in xorg.conf.

Thanks.

---

### Post by Tich666 on 2009-03-21
Setting a virtual resolution works for me in jaunty, see my xorg.conf:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver "intel"
	Option "FramebufferCompression" "on"
	Option "AccelMethod" "UXA"
	Option "Tiling" "No"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

```

However, 3d acceleration which is required for compiz will only work up to a virtual res of 2048x2048, which apparently is because of technical issues (that aren't present for win vista :( ).

I'm using the xorg-edgers ppa and 2.6.29-rc8 kernel, have UXA enabled as you can see from the xorg.conf

Atm I'm running gnome with metacity compositing, so this should work fine for xfce with it's compositing engine (as a compiz replacement) too.

good luck, and report your findings. :)

---

### Post by tgoose on 2009-03-22
I *believe* that even just putting
```
	SubSection "Display"
	EndSubSection

```
in prevents the X server from starting on my computer, whether or not I put anything in it.  Compositing isn't a concern because not only do I have it disabled, but the maximum resolution of each screen is 1024x768 anyway!

Anyway I'm trying your xorg.conf now to see what that yields&#8212;thanks for that!

edit: what's xorg-edgers? Does that only have an effect on certain models of graphics card?

---

### Post by tgoose on 2009-03-22
Great!  Thanks, I think it was the Driver "Intel" that did it!  That works a treat.

---

