---
title: "gutsy stole my sound!"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by ehtoft on 2007-11-15
I only just started using Ubuntu 3 weeks ago-feisty. Then got original CD 7,10, Since I hadn't done all that much to system, I went for a total installation, All looks ok, but no sound, Sound was my main reason to start using Linux! Anybody got any ideas? thanks in advance, eT norway

---

### Post by logos34 on 2007-11-15
start here.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Did you check that nothing is muted?

$ alsamixer

or right-click on master volume applet in panel>open volume control

---

### Post by ehtoft on 2007-11-16
yeah, I checked that out. Still no good. Is there a system monitor program in ubuntu that might find such a problem? eT

---

### Post by infoseeker on 2007-11-16
What sound hardware do you have?  To find out type (at terminal prompt):
```
lspci
```
Audio hardware should be listed.

---

### Post by Ashrael on 2007-11-21
Tried booting from livecd, in my case it workes there! not after install, so there  must be some inbetween....

[http://ubuntuforums.org/showthread.php?p=3805039#post3805039](http://ubuntuforums.org/showthread.php?p=3805039#post3805039)

Still searching, but getting closer!


TIA

---

### Post by ehtoft on 2007-11-22
I've decided to go back to feisty until this all gets figured out. Feisty works fine everytime, though one little thing with sound does make me scratch my head - after installing k3b the sound disappears. remove k3b and all is well. some conflict. I'm too new to all this and must drudge along at my slow pace for now. But, hey! ubuntu is still proving to be much better than I thought, so I'll live with the slow learning curve... Hope you guys figure it out!  eT norway

---

### Post by Ashrael on 2007-11-28
got it working! in my case it turned out to be pulseaudio package that broke recording.. uninstalled that and now i can record again... don't know how i got this package installed...


HTH

---

