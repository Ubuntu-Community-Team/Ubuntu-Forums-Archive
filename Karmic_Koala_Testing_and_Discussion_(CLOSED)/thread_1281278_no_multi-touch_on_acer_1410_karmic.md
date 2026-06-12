---
title: "no multi-touch on acer 1410/ karmic"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xdevnull on 2009-10-03
I have one of the new acer aspire 1410 "netbooks."  I installed karmic today without any problems.  However for some reason there is no multi-touch.  I turned on the multi-touch scroll in prefs and didn't get it (though I really don't want it - mainly I want 2 finger middle click).  I know the hardware is capable from what it was doin ging vista.  

Any ideas?

lsmod shows a psmouse; 
here's xinput:
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
	Type is TOUCHPAD


Thanks

---

### Post by deemoowoor on 2009-10-09
Same problem here with Acer 1410. It's not that I'd really need it, but it would be nice to know, if it will even work.

---

### Post by Zorael on 2009-10-09
Copied from another thread;

> **me][QUOTE=HankB said:**
> Can you provide the particulars for this? I have not yet figured out how to get the "tap upper right for middle mouse click" working on my Eee PC 901 with Karmic. Scrolling and left/right click work fine.

thanks,
hank
See [http://ubuntuforums.org/showthread.php?p=7643273&postcount=2](http://ubuntuforums.org/showthread.php?p=7643273&postcount=2). The prop you want to modify is "Synaptic Tap Action".

```
Synaptics Tap Action (267):     2, 3, 0, 0, 1, 2, 3
```
If memory serves the first figure is top-right, then bottom-right, then top-left, then bottom-left. 1 corresponds to the left mouse button, 2 to the middle and 3 to the right.

The last three figures are multi-finger taps, I think; one finger, two fingers, three fingers (if the pad supports it).[/quote]

So you want to set the next-to-last figure to 2 to get two-finger middle mouseclicks.

---

### Post by Ryan Yo on 2009-10-16
I'm also having this problem. I've got an Asus EeePC 1005HA-P that has a multi-touch trackpad but setting the 'Two-finger Scrolling' option in the mouse settings doesn't work at all.

Edit: I'm running Ubuntu Netbook Remix. Anyone tried this on the desktop version of Ubuntu?

---

