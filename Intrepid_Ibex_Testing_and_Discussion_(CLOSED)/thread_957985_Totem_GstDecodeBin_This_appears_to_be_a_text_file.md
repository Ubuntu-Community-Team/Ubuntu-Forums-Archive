---
title: "Totem: GstDecodeBin: This appears to be a text file"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2008-10-24
Has anyone run into this? I'm unable to load m3u files into Totem, getting this error all the time.

---

### Post by ciscosurfer on 2008-10-24
Does this happen with any/all m3u files w/Totem?  You could file a bug on Launchpad.

---

### Post by ubulette on 2008-10-25
I filed a bug in Launchpad a while ago: [https://bugs.launchpad.net/totem/+bug/251669](https://bugs.launchpad.net/totem/+bug/251669).
There has been a confusion between regular m3u and extended m3u so I tracked this down and opened an upstream bug too: [http://bugzilla.gnome.org/show_bug.cgi?id=556060](http://bugzilla.gnome.org/show_bug.cgi?id=556060) with more details.
It seems fixed upstream now (somehow, lp failed to reflect the status so i didn't notice sooner). I'll give the patch a try and see if/how ubuntu can take it.

---

### Post by Enigmatic on 2008-10-25
So is this going to be included in Ibex, or hopefully shortly after?

---

### Post by ubulette on 2008-10-26
Ok, patch tested, it's all fine.
Fix is in my [PPA]("https://edge.launchpad.net/~fta/+archive")

> **Enigmatic said:**
> So is this going to be included in Ibex, or hopefully shortly after?

I don't know yet.

---

### Post by ubulette on 2008-10-27
> **Enigmatic said:**
> So is this going to be included in Ibex, or hopefully shortly after?


not critical enough for a last second upload according to the release manager so I'll do a SRU (Stable Release Update).

---

