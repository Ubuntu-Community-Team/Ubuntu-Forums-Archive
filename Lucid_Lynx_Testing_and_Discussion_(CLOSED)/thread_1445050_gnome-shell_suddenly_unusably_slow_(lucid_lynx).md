---
title: "gnome-shell suddenly unusably slow (lucid lynx)"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pjc007 on 2010-04-02
Hi all,

I have been playing with gnome-shell (a self-built version), and until today it was working great, and I was happy to use it as my primary desktop environment, albeit on my test machine...

As of today, having taken the latest updates from the lucid lynx, my self-built gnome-shell is suddenly unusably slow.

I attempted a rebuild in case there'd been an incompatibility introduced, but it's still unusable.

Has anybody else experienced similar effects?

I'm running Lucid Lynx, with the latest updates from the repos, and gnome-shell with a jhbuild from this morning.

Thanks in advance -- note, I'll ask about this over on gnome forums as well...

-Paul.

---

### Post by Sennaista on 2010-04-02
Same problem here, although I installed it from this [ppa]("https://launchpad.net/%7Ericotz/+archive/testing").

---

### Post by pjc007 on 2010-04-15
Well - in spite of nobody responding on either board, I've found a solution -- or at least a work-around, on this page:

[http://live.gnome.org/GnomeShell/SwatList](http://live.gnome.org/GnomeShell/SwatList)

It appears that the issue is:

**Slow updates**: If you are using an Intel GPU without kernel mode-setting, and you experience very slow updates (e.g. 1 second intervals in animations) then you might try exporting "CLUTTER_VBLANK=none" in the terminal before running gnome-shell.

Quite why the Intel GPU kernel mode-setting should suddenly stop working in a later release of lucid, is beyond me, though!

-PJC

---

