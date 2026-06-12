---
title: "Sound is broken"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DevilInPgh on 2009-09-23
When I tried to play an audio file in today's Karmic build, I could not get any audio output.  On top of gnome-volume-control not working (and I hope is a known issue), alsamixer also decided to crap out on me.  This is the code output I received:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```
In previous builds, alsamixer worked for me, but now it doesn't.

---

### Post by jmdsdf on 2009-09-23
Try reverting udev to 147~-1 and restart. Does that fix it? It worked for me.

Run "sudo dpkg -i /var/cache/apt/archives/udev_147~-1_i386.deb", assuming you're 32-bit and you have the old version in your cache. Then place a hold on udev until this bug is fixed.

Also, could someone open a bug report about this? I'm using a Creative Labs SB Audigy and the latest udev update broken something. I can still cat a wav file to /dev/dsp to hear sound, but alsamixer gives the exact same error, play and aplay also don't work. No audio card is detected by pavucontrol.

---

### Post by DevilInPgh on 2009-09-23
The downgrade broke initramfs-tools.

---

### Post by jmdsdf on 2009-09-23
I may also have downgraded initscripts, sysv-rc and insserv in my quest to get it fixed. HTH?

P.S. This fix may not be for the faint of heart, at one point my system was only booting to a recovery console and I had fun  trying to get dpkg to run so I could reinstall some packages (the PATH variable wasn't set properly -- the trick was to use "su -" to get to a proper login shell, I wasted about one hour on my life fixing this sound issue on my system. It reminds me why I shouldn't install Alpha versions of Ubuntu!)

---

### Post by talkingwires on 2009-09-24
> **jmdsdf said:**
> t reminds me why I shouldn't install Alpha versions of Ubuntu!True, but the Beta is going to be dropping soon. That's the stage where as many people that can test it, should. Karmic's been strange. Usually it gets rough around Alpha 3 or Alpha 4, and stabilizes before the Beta. This time around, it seems like the breakage is gonna keep on coming right up until the Beta Freeze.

---

