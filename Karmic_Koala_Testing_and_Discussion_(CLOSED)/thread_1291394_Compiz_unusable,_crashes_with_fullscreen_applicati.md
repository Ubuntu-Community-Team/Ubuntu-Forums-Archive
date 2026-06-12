---
title: "Compiz unusable, crashes with fullscreen applications"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tim1 on 2009-10-14
Compiz crashes all the time, I can reproduc ith when an application goes fullscreen like totem, evince, firefox, quake live...

I reported a bug here but nobody seems to care:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/438873](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/438873)

Does anybody else have this bug?

---

### Post by NRDNick on 2009-10-14
Yes I've been getting random freezes playing W:ET with compiz enabled. This had ceased for a while but seems to be back again with recent updates. I'm using the nvidia 185 that's in the repos, and I noticed that it was updated the other day. I really don't have a clue as to what's causing it, sometimes the game will just hang for 2-5 seconds, other times it's a full on lock up and I have to alt+sysrq REISUB to reboot the system. 

I've also been playing around with the sync to vblank option in compiz config, and I just read recently that having it enabled can reduce the load that compiz puts on your cpu. Going to leave it on for awhile and see if the freezes go away. It could have been that it was only crashing when I had the option disabled. I'll try to report back here if I find anything new.

Edit: Well scrap the vblank idea I had, just froze again on me with it enabled. For troubleshooting purposes, what vid card and driver are you using?

---

### Post by null_pointer_us on 2009-10-14
I saw a few options in Compiz Settings Manager related to fullscreen and/or video playback compatibility. Check under Utility -> Workarounds, General -> General Options, for example. Maybe this'll help, maybe not.

Sync to Vblank setting really just reduces tearing by preventing screen updates in the brief periods when your monitor is refreshing. This shouldn't affect stability; its primary use is to improve image quality.

---

### Post by NRDNick on 2009-10-14
I just noticed there is a new version of compiz out, thanks to cdahmedeh and the thread he just posted on it here [http://ubuntuforums.org/showthread.php?t=1291460]("http://ubuntuforums.org/showthread.php?t=1291460"). 

Reading through the change log I noticed that the 'force synchronization between x and glx' is now enabled by default. I know I've had this setting checked before, and recently disabled it. So I'll see if having it enabled stops the lock ups. 

The new version seems to have a lot of memory leaks fixed in it, which seems more likely to be the culprit of these crashes. So if all else fails, I guess I'll be updating to the newer version and crossing my fingers.

---

