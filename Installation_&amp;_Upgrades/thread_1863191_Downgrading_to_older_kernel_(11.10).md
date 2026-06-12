---
title: "Downgrading to older kernel (11.10)"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by nightfever on 2011-10-17
To make my snd-emu10k1 card work, I have to recompile ALSA.
For some reason compiling does not work with v.3.x.x kernel.
How can I downgrade to 2.9?

---

### Post by nightfever on 2011-10-18
Anyone? Please.

---

### Post by youngunix on 2011-10-18
dude, there is no downgrade. 

if you have tried to fix it and it didn't work, then the best you can do is save the data you need and do a fresh install.

---

### Post by nightfever on 2011-10-18
> **youngunix said:**
> dude, there is no downgrade. 

if you have tried to fix it and it didn't work, then the best you can do is save the data you need and do a fresh install.
Even with a fresh install it won't work by default.
To make it work I have to run a script (is't here somewhere, Alsa Upgrade Script Redux) which basically re-installs alsa.
But alsa compilation won't work with v.3 kernel due to some missing libraries and stuff.

---

### Post by youngunix on 2011-10-18
in that case, you need to check if there is an update for ALSA that works with kernel v3+.
as you can see in the forums A LOTS of upgrades have failed and/or followed by many issues, so give it a few days while the developers are working on fixing the bugs. 
also app developers need to launch updates for their software to work properly with the new ubuntu/kernel.

---

