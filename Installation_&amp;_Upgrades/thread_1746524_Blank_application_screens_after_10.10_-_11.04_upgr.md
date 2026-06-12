---
title: "Blank application screens after 10.10 - 11.04 upgrade"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by tokazowc on 2011-05-01
Stupidly did the automatic upgrade to 11.04 last night.  Didn't go TERRIBLY wrong, but on many applications I just get a blank white screen.  Even on some that launch properly, if i minimize or switch between apps, I get that same blank screen.  App is working (clicked around in Evolution and Title changed), but I can't see anything.  Happens both in Unity and Classic.

Is this a simple fix, or yet another fresh install?

---

### Post by mörgæs on 2011-05-02
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by tokazowc on 2011-05-02
Solved.

Problem was with the nvidia drivers.

First found some leads in this thread:
[http://ubuntuforums.org/showthread.php?t=1743386&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=1743386&highlight=nvidia)

Which lead to this post:
[http://ubuntuforums.org/showpost.php?p=10742896&postcount=4](http://ubuntuforums.org/showpost.php?p=10742896&postcount=4)

That helped a bit, but after 2 or 3 apps were open, it was still blank.  Activated nvidia-173 driver and all seems good now.  Not sure exactly which step did it....I'm guessing that it was just going back to the older driver as I'd seen that posted somewhere along the line.  Driver is still showing as "Active but not in use"

---

### Post by mörgæs on 2011-05-02
Good, please mark the thread 'solved' using 'thread tools'.

---

### Post by tokazowc on 2011-05-02
> **mörgæs said:**
> Good, please mark the thread 'solved' using 'thread tools'.

Was looking for that before.  Thx

---

