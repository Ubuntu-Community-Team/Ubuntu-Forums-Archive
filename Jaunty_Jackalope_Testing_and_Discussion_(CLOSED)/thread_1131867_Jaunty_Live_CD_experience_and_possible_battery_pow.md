---
title: "Jaunty Live CD experience and possible battery power bug"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Denis on 2009-04-21
Hi everyone

I just tested the Jauny Release Candidate on live CD. My first impressions are very positive. The system feels very snappy and quick (even on CD). I'll first discuss a bug I've seen. Then I'll talk about some thinks that caught my attention. 

First of all Jaunty seems to pick up the USB signal from my UPS (backup power) and shows the amount of power left. It also lets me chose what to do when the battery is running out. I've never seen this in Intrepid, so I assume my MGE UPS is now supported. Nice work ;)

One problem is that the icon states "computer is running on backup power" from the start, while in fact it is running on regular AC. When backup power is used everything works fine. When I plug the power back in the icon disappears. This is slightly confusing because I couldn't find it any more. The statement that the computer was using backup power at the start was clearly **inaccurate**, I hope it is fixed in the final release (or the installed version). 

Automatic detection of the network works very well. I can also see my IP-address in a GUI, which I find useful. On Intrepid the network doesn't show up, although it works fine. Maybe this could be fixed by doing a clean install instead of an update. 

In my opinion the splash screen hasn't really become more pleasant. The previous one was just as good. When running from the live CD the indicator bar goes from left to right (don't know about the full install). This doesn't give the user much information. I think it should be avoided. 

Another thing I noticed is the "fade" when changing desktop backgrounds. It's a nice effect, but it takes a bit too long I think. Also there is a terrible lag between clicking on a background and the actual change (again maybe this happens because Ubuntu is running from CD). Also I think we don't need the fade when changing "style" (tiled, zoom, centered...).

The standard subpixel smoothing for fonts doesn't look good here. The fonts are slightly blurry and look bold. Changing hinting to medium makes it look excellent. I don't know why "slight" was chosen as the default. 

Gimp's editing windows are now grouped together with the image. I think it's an improvement. No need to click three times to get the Gimp's windows tot the top anymore. 

Pidgin has a smaller version of the default smiley theme. I really like smaller icons that don't displace the text :) I haven't tested it though. 

The keyboard shortcuts window has more options. I can now assign my "pause break" key again. No need to use xbindkeys anymore. 

Jaunty looks like a very clean version. I hope the update will go just as well. There are no big changes, but some slight improvements definitely make it worth updating/installing.

Thanks for reading, see you later.

---

