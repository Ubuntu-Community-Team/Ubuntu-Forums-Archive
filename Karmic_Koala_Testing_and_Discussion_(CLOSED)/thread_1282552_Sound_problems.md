---
title: "Sound problems"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tlu on 2009-10-04
I'm running Karmic Koala 64 bit, and I'm having strange sound problems.

Playing wav or mp3 files with kaffeine works, but I can't hear any sound when using Rhythmbox or Songbird (neither the 1.2.0 version from getdeb.net nor 1.5.0 from the Songbird ppa). They used to work under Jaunty, though.

My hardware: cat /proc/asound/cards shows

```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa000000 irq 22
```

And head -n 1 /proc/asound/card0/codec* shows:

```
Codec: Realtek ALC888
```

But I don't think that my problem is hardware related as kaffeine works and I can also hear system sounds.

The audio backend is xine. 

I would appreciate any hints.

---

