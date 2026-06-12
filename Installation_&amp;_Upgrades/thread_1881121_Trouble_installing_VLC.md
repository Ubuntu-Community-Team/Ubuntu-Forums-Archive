---
title: "Trouble installing VLC"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Goranson on 2011-11-14
Hi. I'm rather new to Ubuntu, so if my problem has a rather obvious solution, or if I'm posting this in the wrong section, I apologize. Anyway, I was downloading VLC player and the download froze before it was finished. I restarted the computer, thinking I'd delete it and try reinstalling it again, but when I try to delete it I get an error message reading:

"**Previous installation hasn't been completed**
The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

I have no idea whatsoever as to how to repair this. Any help would be appreciated.

---

### Post by hansdown on 2011-11-15
Welcome to the forum, Goranson.

No need to apologize, it's all good.

Restarting, during an install, is not a great thing, as far as, achieving the objective.

It results in, corrupted files.

Did you try the original install, with.....

synaptic, ubuntu software center, apt-get?

---

### Post by Goranson on 2011-11-15
My original install attempt was with Ubuntu software center.

---

### Post by hansdown on 2011-11-15
> **Goranson said:**
> My original install attempt was with Ubuntu software center.

O.K.

I don't have a lot of experience with software center, but in synaptic, you can fix broken packages, by clicking...

```
custom filters, then broken> fix broken packages.
```

---

### Post by raja.genupula on 2011-11-15
open your terminal and then do this

```
sudo apt-get install -f
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
```

all the best

---

