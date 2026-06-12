---
title: "[SOLVED] radio screenlet ,plays but no sound"
date: 2008-06-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-06-23
this is not the normal no sound problem , a updates a couple of days ago killed sound in the radio screenlet , mplayer plays files ok and I can see the stream coming in on netmon , when I hit the play button on the screenlet it starts 2 instances of mplayer but no sound comes out . reported bug #242520 , anyone else having or solved this ?

---

### Post by soccerboy on 2008-06-23
fixable by changing the sink for the application according to this thread [http://ubuntuforums.org/showthread.php?t=833825](http://ubuntuforums.org/showthread.php?t=833825) perhaps?

---

### Post by ronacc on 2008-06-23
the screenlet uses mplayer to play the stream and sound in mplayer is normal , I switched everything to alsa when the pulse problem started .

---

### Post by ronacc on 2008-06-23
update , while mplayer does play mp3's etc it will not play .ram streams appearently the real media codec went missing . problem is not with the radio screenlet.

edit closed bug

---

