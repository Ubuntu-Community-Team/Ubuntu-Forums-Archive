---
title: "Cant play sound from Firefox &amp; Banshee at same time"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bear24rw on 2009-09-02
Does anyone else experience this problem? I can only have one application playing sound at a given time. For instance, if I have firefox open watching youtube and then go to open banshee, bashee will refuse to play anything and just sit at Idle on the seek bar, but if I close firefox sound returns to banshee, i can then reopen firefox but youtube will have no sound..

anyone know a fix for this?

---

### Post by Suiname on 2009-09-03
I have the same problem, I'll let you know if I find anything

---

### Post by Suiname on 2009-09-03
I found a fix, it has to do with flash.  install the package libflashsupport:
```

sudo apt-get install libflashsupport
```I'm using 32-bit 8.04 and this solved the problem for me.

---

### Post by blazemore on 2009-09-03
Oh I've always had this on everything except OpenSuse. I think it's PulseAudio.

---

### Post by OliW on 2009-09-03
There is also a newish bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411962](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411962)

Fix that worked for the OP (and me) was deleting ~/.pulse

---

