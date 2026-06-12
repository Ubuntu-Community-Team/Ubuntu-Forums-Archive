---
title: "totem and compiz issue (video playback)"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nimes on 2008-10-17
hi,

this picture saying for everything

how to fix this error??

---

### Post by EnigMattic on 2008-10-25
Having the same problem.
The video also flickers when the mouse is in motion.

---

### Post by EnigMattic on 2008-10-25
Try this, from [http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html]("http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html"), it worked for me!!!:

o Open a terminal and type “gstreamer-properties”. Press Enter.

o Click the Video tab.

o Under Default Video Plugin select “X Window System (No Xv)”.

o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).

o Click Close

---

