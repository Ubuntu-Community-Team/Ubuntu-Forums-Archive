---
title: "Notify-OSD Works Intermittently"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by insertnewsn on 2009-03-30
Hey everyone,

I know that Jaunty is still beta software and there are no guarantees, but I've been having a weird problem with notify-osd lately since upgrading to the beta.

When I first installed Jaunty, the notifications worked perfectly. I don't know if I changed something I shouldn't have or what, but sometimes when I boot into Ubuntu, notify-osd doesn't work, and is instead replaced by the old-style notifications. I switched my theme back to Human but this problem persists nonetheless.

What's weird about this is that it seemingly occurs randomly. If I restart 2-3 times, notify-osd will start to work again. 

At first I thought it might have something to do with me enabling UXA in my xorg.conf file, but disabling it has no effect...notify-osd will still work intermittently.

Has anyone else run into this problem before?

---

### Post by insertnewsn on 2009-04-01
Bumpity Bump..Still having the problem. I just logged out twice and only on the 2rd logout/login did notify-osd begin to work for me.

---

### Post by insertnewsn on 2009-04-05
Bump. Do the Bumpy bump.

---

### Post by insertnewsn on 2009-04-07
Bump.

Sorry, but am I really the only one who has had this problem with Jaunty? :-/

---

### Post by dirtylobster on 2009-04-07
Seems so. :)

Does ~/.cache/notify-osd.log contain anything?

---

### Post by insertnewsn on 2009-04-07
Thanks for your reply dirtylobster!

~/.cache/notify-osd.log doesn't contain any data at all...

One weird thing that I noticed, however, is that if I continually press the "Volume Down" button on my keyboard (XF86AudioLowerVolume) when my system starts up, Notify-OSD will ALWAYS load correctly. If I don't do this, Notify-OSD may or may not work.

Any ideas? Again..thanks for your reply!

---

### Post by insertnewsn on 2009-04-08
Not that anyone else has had this problem, but the fix was disabling the Avant-Window-Navigator (AWN) notification applet.


I didn't even realize that was enabled. My bad.

---

