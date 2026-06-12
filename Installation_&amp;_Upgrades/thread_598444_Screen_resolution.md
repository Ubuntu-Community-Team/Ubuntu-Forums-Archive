---
title: "Screen resolution"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Jim Lewis on 2007-10-31
My second question:

Now that I'm installed, are there only 2 choices for screen resolution (System/Preferences/Screen Resolution) available -- 800x600 or 640 x 480 -- because I still have to move the entire box to see any "Next" or "Forward" buttons?

---

### Post by taurus on 2007-10-31
What kind of graphic card do you have?  Maybe you need to install a driver for it before you can go to higher resolutions.

---

### Post by traderpats on 2007-10-31
There are also settings located at System/Administration/Screens and Graphics.  It should also show what card is installed.

---

### Post by Jim Lewis on 2007-10-31
> **traderpats said:**
> There are also settings located at System/Administration/Screens and Graphics.  It should also show what card is installed.

I don't see any "System/Administration/Screens and Graphics."

---

### Post by Jim Lewis on 2007-10-31
I got it fixed.  I needed to get a restricted device working.  Thanks all.

---

### Post by compcomp on 2007-11-03
Go to the terminal and type this:

```
sudo gedit /etc/X11/xorg.conf
```

Then type you your password(if he need it).

you must see this:
```

Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		[COLOR="Red"]"1600x1200@60"	"1600x1200@65"	"1400x1050@75"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"[/COLOR]
	EndSubSection
EndSection

```

copie the red  text after the word Modes (there stand by you only "800x600@..." and "640x480@...")

Read first totaly my post

Press Ctrl+Alt+Backspace
And then go look at the resolution window(System>Preferences>Screenresolution)
:)


Compcomp

---

