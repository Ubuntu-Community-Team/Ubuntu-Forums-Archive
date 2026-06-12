---
title: "Regression in 2D graphics in KMS (xorg-edgers)"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-03-28
If I choose KMS I get, as of yesterday, or so, a huge regression in 2D display, i.e. browsers and other windows, terminal also, redraws in slow motion, like sheets are beeing dropped... If I go in UMS, everything is OK.  I've tried (almost) everything, short of ppa-purge of xorg-edgers, as I'm not sure where is the reason for this. If I add random crashes and being unable to get a proper shutdown, my Lucid experience-factor is, nowdays going down very fast...
(ATI HD 3650 512M)(Lucid up-to-date)

---

### Post by Longinus00 on 2010-03-28
Isn't xorg-edgers a bleeding edge (unstable) testing repo?

---

### Post by nanog on 2010-03-28
Not seeing this at all but I'm using noveau.

---

### Post by zika on 2010-03-29
It seems that it is solved, but I'll wait for some time before I mark it [solved]...

Update: Nope, it happened again... Somehow Rhythmbox is involved...

Update: It seems that I've found a culprit. Guess what: plymouth! Once I've eliminated "splash" from kernel line, regression is, I hope, gone...

Update: No, it's not the solution. But, it occurs later in the session. I'm a bit puzzled...

---

### Post by moviemaniac on 2010-04-04
If I were you I'd try a newer mainline kernel, preferrably 2.6.32-2 or 2.6.34-rc3. There's lots of stuff not really working in the graphics department with Ubuntu's -32 kernel. I also had flickering and image distortions using KMS (ATI 2600XT) on Ubuntu's -32 (on top of the random freezes) - these problems are gone since I switched to -34-rc*

---

### Post by zika on 2010-04-04
> **moviemaniac said:**
> If I were you I'd try a newer mainline kernel, preferrably 2.6.32-2 or 2.6.34-rc3. There's lots of stuff not really working in the graphics department with Ubuntu's -32 kernel. I also had flickering and image distortions using KMS (ATI 2600XT) on Ubuntu's -32 (on top of the random freezes) - these problems are gone since I switched to -34-rc*Slowdown was present in 2.6.34-999, also. I'm always on "current" from mainline... I'm checking .32 and .32-ck just to be sure if .34 is to blame, but it was not... Problem was solved by itself in previous couple of days but I was not brave enough to mark it [solved] yet...

---

