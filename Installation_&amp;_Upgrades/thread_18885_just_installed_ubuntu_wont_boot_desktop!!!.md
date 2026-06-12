---
title: "just installed ubuntu wont boot desktop!!!"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by mrstimpson on 2005-03-09
Im interested in linux again, while waiting for another to download I got ubuntu of a mag.

I installed then Im left with a command line interface.

sam@ubuntu: $


I tried typeing startx

but get command not found?

how do I get to desktop?!!!

its a centrino laptop, with intel extreme graphics

---

### Post by djjazzyjeff on 2005-03-09
Same thing happened to me yesterday. System is Compaq Evo N800c, ATI Mobility Radeon 7500 video, 1024x768 LCD panel. The specific error message on running startx:

/usr/X11R6/lib/X11/xinit/xserverrc: line 2: /usr/bin/X11/X: No such file or directory
/usr/X11R6/lib/X11/xinit/xserverrc: line 2: exec: /usr/bin/X11/X: cannot execute: No such file or directory

It looks like an incomplete install of X? If so, how do I selectively reinstall it? I have an XF86Config-4 that should work for this hardware. I'd really like to get this running and try out Ubuntu, any help is appreciated........Jeff

---

