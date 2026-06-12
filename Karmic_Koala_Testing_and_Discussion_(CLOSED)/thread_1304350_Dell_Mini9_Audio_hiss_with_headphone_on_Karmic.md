---
title: "Dell Mini9: Audio hiss with headphone on Karmic"
date: 2009-10-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fedleo on 2009-10-29
When you put headphone jack in an hissing sound starts from speakers, if you remove headphone the noise stops immediately. The sound in headphone is quite perfect.
I'm on a dual boot machine (9.04 and 9.10), with jaunty with kernel 2.6.28 sound is perfect with no issues. Audio settings are the same on both OS. I suppose it's a pulseaudio/kernel settings related problem (Karmic now uses 2.6.31-14 kernel) but can't be sure.
Tested it with mics muted and all audio set to zero. No luck.
lspci reports:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Could someone confirm this issue on Mini9 before I start a bug on launchpad?

Thanks.

---

