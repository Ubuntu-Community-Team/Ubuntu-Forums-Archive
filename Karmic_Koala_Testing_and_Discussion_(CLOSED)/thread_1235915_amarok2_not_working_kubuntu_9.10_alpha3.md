---
title: "amarok2 not working kubuntu 9.10 alpha3"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Arijit_Kundu on 2009-08-09
Hi friends,

I am using 9.10 alpha 3 for about 4 days. It is working nicely except some problems with amarok and network manager. 
amarok (2.1.1) is not working normally. it is opening only with sudo. Does anyone else have the same problem as mine?

I have also made a bug report at 
[https://bugs.launchpad.net/bugs/411175](https://bugs.launchpad.net/bugs/411175)

any ideas?

---

### Post by overdrank on 2009-08-09
Moved to Karmic Koala Testing and Discussion

---

### Post by taavikko on 2009-08-10
Remove the amarok config folder from ~/ so it resets to defaults.
I'll suspect that something has corrupted its permissions. Thus requiring sudo to work.

---

### Post by Arijit_Kundu on 2009-08-10
thanks!

It solves the problem :). But, how this permission can be changed? is it a bug or something?

---

### Post by maestrobwh1 on 2009-08-26
Is amarok broken?  I cannot play m4a or mp3 files.  Mplayer plays these.  Not sure if mplayer relies on ffmpeg rather than faac/faad.  Peculiar that mp3 files don't play on Amarok.

Using exaile for now.  Uses gstreamer.

Also perhaps related: m4a files created with soundkonverter don't play.  

Faac/Faad issue perhaps?

---

### Post by maestrobwh1 on 2009-08-27
Not solved but worked around - found a ppa for amarok 1.4 - I always liked the interface better anyway;-)

---

