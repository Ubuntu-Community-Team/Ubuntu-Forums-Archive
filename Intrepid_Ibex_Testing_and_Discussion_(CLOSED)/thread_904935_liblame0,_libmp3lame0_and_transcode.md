---
title: "liblame0, libmp3lame0 and transcode"
date: 2008-08-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klange on 2008-08-29
Got a bit of a problem with these three in the repos.
**liblame0** is slightly older - but it's what everything depends on. Except the current update for **transcode**, which depends on **libmp3lame0**. The problem is, **libmp3lame0** conflicts and replaces **liblame0** without providing it or having the other packages depend on **liblame0 | libmp3lame0**, so it breaks a bunch of stuff:

cinellera *(which we can ignore, it's not in the repos)*
devede - *definitely not good*
gstreamer...ugly-multiverse
mencoder
*and worst of all: *mplayer

---

### Post by Nullack on 2008-08-29
The MOTU's attitude about mplayer and ffmpeg is problematic. You can see the situation with their reponses in the bug I filed about upgrading mplayer. If you want to use mplayer or ffmpeg your best off forgetting about using packages and doing your own compiles.

---

### Post by stmiller on 2008-08-29
What about medibuntu packages? Do they help or is it still broken with medibuntu added?

---

### Post by Nullack on 2008-08-29
I seek to aid testing of Ubuntu so I dont add external repos. Also it eliminates any risk of having to trust an external source.

---

