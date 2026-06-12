---
title: "GUI for timidity"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-08-24
Is there a GUI for the timidity program ?

The timidity program is the only way I have found, so far, that will play MIDI files.

The KMID program (which has a GUI) will not play them.

Thanks.

---

### Post by Fibonacci on 2006-10-06
Yes, there is a GUI for TiMidity, but I have never gotten it to work.
However, KMid works well for me, using TiMidity as a sort of daemon under it.
Start TiMidity with:
```
timidity -iA -B2,8 -Os -EFreverb=0 > /dev/null &
```
Then look in the KMid menus, look for "configure MIDI ports" or something remotely like that (sorry, I don't have KMid right now so I cannot tell you exactly), and choose one of the TiMidity ports.
KMid should be working like a charm now.

---

### Post by wpshooter on 2006-10-07
Thanks.

I did finally get some sound although the quality was not all that good.

But may I ask why is it that it is necessary to seemly have to install and combine what appears to me to be two different programs in order to get this to work ?

Should the KMID program not install everything that it needs in order to work properly ?

P.S. - Also, does this mean that if I restart the system that I would have to reissue the timidity command each new session in order to have this work ?

Thanks.

---

