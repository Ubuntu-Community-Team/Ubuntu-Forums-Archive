---
title: "Excessive heat running Compiz on Intel video..."
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-07-29
I have a Lenovo T61 with Intel GM965 video.  It seems that after a few hours of use, running with COmpiz enabled generates excessive heat that degrades video performance.  If I turn off compiz, it runs much cooler and never has any video issues.  I like the cube for productivity purposes, but unless something changes, I may never be able to run compiz on this machine.  Never had this issue with Jaunty or any previous release with compiz.

Anyone else seeing something similar?

---

### Post by Kobalt on 2009-07-29
Intel GPU drivers are drastically different from Jaunty to Karmic. It may be the cause of your overheat, not compiz itself.

---

### Post by mariner09 on 2009-07-30
Turns out that Metacity was the root of my problems.  When I switch to Emerald, all is well...

---

### Post by wayne_cat on 2009-07-30
> **mariner09 said:**
> Turns out that Metacity was the root of my problems.  When I switch to Emerald, all is well...


[http://ubuntuforums.org/showthread.php?t=1222849](http://ubuntuforums.org/showthread.php?t=1222849)

---

### Post by mariner09 on 2009-07-30
I read that bug report last night as well.  Any target for a fix?  Not that I mind using Emerald...

---

### Post by wayne_cat on 2009-07-30
> **mariner09 said:**
> I read that bug report last night as well.  Any target for a fix?  Not that I mind using Emerald...

There is a fix ... but we still have to wait for this version

[http://bugzilla.gnome.org/show_bug.cgi?id=588119](http://bugzilla.gnome.org/show_bug.cgi?id=588119)

Solved the problem for my system:

[http://ubuntuforums.org/showthread.php?t=1226658](http://ubuntuforums.org/showthread.php?t=1226658)

---

