---
title: "Totem muted"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lazka on 2009-10-03
The totem volume button is greyed out.. video is working.. audio is not.
Works in every other app except totem.

I have no pulseaudio btw.

---

### Post by lazka on 2009-10-03
bump

---

### Post by blk_jack on 2009-10-03
I was in the same boat and what worked for me was making sure every part of pulseaudio was removed via synaptic.

gstreamer0.10-pulseaudio was the only package left that I hadn't removed, but once I got rid of it, everything worked.

Make sure you also go into gstreamer-properties and set everything to Autodetect so that it's not referencing pulseaudio anymore.

---

### Post by VMC on 2009-10-03
From a terminal type **alsamixer** and make sure nothing is muted.

---

### Post by lazka on 2009-10-05
Deleting gstreamer0.10-pulseaudio did the trick. Thanks blk_jack :)

---

