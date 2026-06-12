---
title: "Videos have green tint"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by adam-red on 2009-10-03
Has anyone noticed their video files being played back with a green tint? I upgraded to Karmic beta last night because of sound issues in Jaunty and my webcam worked straight away with skype 2.1 beta. I know this isn't production, but flash video and movs work online on youtube for example, but not when you're playing them back through vlc/totem/xine. Can't be application specific as I've tried three different media players. X64.

Thanks

---

### Post by x0XOx on 2009-10-03
Do you have a NVidia card?

---

### Post by nhasian on 2009-10-03
in VLC go to tools->preferences->video change the output from default to x video extention or x11.  exit and restart vlc and see if that fixes your green tint problem.

---

### Post by adam-red on 2009-10-03
Changing the output to X11 works for vlc. I'll just play videos in that from now on. It's an nvidia card.

---

### Post by BoyOfDestiny on 2009-10-03
For Totem ("Movie Player" under Applications -> Sound and Video)

Edit -> Preferences

Click the Display tab,

there are 2 sliders under Color Balance.

Adjust it accordingly, and that should solve it.

---

### Post by adam-red on 2009-10-03
Sorted now, thanks

---

### Post by motang on 2009-10-04
Chaning the hue to be the same as the other three solves this issue with Totem.

---

### Post by theanswriz42 on 2009-10-04
Another solution would be to change the default video output in gstreamer-properties to X Window System (No Xv)

---

