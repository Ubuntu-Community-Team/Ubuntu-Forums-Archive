---
title: "IBM laptop with Trackpoint - Enable scroll"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-30
Hi :)

I would really appriciate some help on this. Scroll dosn't seem to be working on my IBM X31. It's not a mouse but a Trackpoint - but hopefully someone can help my anyways :-)

 - Thanks in advance

---

### Post by jemt on 2005-07-31
Solved. I added these linies to my /etc/X11/xorg.conf :

Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"

---

