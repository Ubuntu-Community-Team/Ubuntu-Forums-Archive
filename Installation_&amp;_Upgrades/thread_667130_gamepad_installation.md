---
title: "gamepad installation"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by andale on 2008-01-14
I came across the site:
[HTML]http://onlyubuntu.blogspot.com/2007/03/how-to-set-up-gameportgamepad-or.html[/HTML]
and it took care of the job pretty well, the really simple thing i was missing is to install jscalibrate, I couldn't find a mention of it anywhere before, so I thought I'd link that and tell you how well I did.
I have the little white FT8D91 box that I got from Wal-Mart, I have 1 of each controller (PS2 DS, XBOX, and GC) plugged into it and upon running jscalibrate found that already the ps2 controller worked fine. However, the xbox and gamecube controllers seem to do nothing.
I also have a usb-modded xbox controller plugged into 1 of it's usb ports, that worked fine after using 'sudo modprobe xpad'. I also have a sidewinder plugged into my Ensoniq sound card but even though 'lsmod' shows my sidewinder, it doesn't appear to function.
jscalibrate lists /dev/joy0, 1, & 2, that's 3 controllers, but one appears to do nothing, I am guessing it is the sidewinder as i never did anything towards installing my soundcard, just plugged it in.

This isn't much help at all, I realize, but I'm hoping to get a ball rolling to get all the info on these things out there, it seemed to me like a pretty serious lack of info on this stuff, maybe cuz it's usually straight-forward, i don't know. But I've also never had epsxe run so well as it does in linux.


EDIT:

Okay, so while jscalibrator does see 2 of the five, but epsxe doesn't seem to see any of them, trying to get some other plugins to test it, but haven't yet.

---

