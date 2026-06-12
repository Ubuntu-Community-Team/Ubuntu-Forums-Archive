---
title: "No sound in flash under firefox"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2009-09-14
Has anyone else noticed their flash sound disappearing? Was working fine until a few days ago. Works fine in other apps.

---

### Post by foxmulder881 on 2009-09-14
I'm not running Ubuntu at the moment in favor of Fedora, but I know my Fedora 11 system received Firefox 3.5.3 just a few days ago. Perhaps it was the Firefox update on Karmic that has done it. :confused:

---

### Post by Enigmatic on 2009-09-14
I am also running 3.5.3. That could certainly be a factor.

---

### Post by Enigmatic on 2009-09-14
Looks like the individual application volume was turned down under sound preferences.

---

### Post by DLGandalf on 2009-09-15
That's the strange thing, it doesn't even show up in my volume-manager.
It's just playing as loud as it can, I can't control it.

---

### Post by psyke83 on 2009-09-15
Most likely, the 32 bit PulseAudio ALSA plugins aren't functioning. See this thread (and the bug report contained within): [http://ubuntuforums.org/showthread.php?t=1265537](http://ubuntuforums.org/showthread.php?t=1265537)

---

