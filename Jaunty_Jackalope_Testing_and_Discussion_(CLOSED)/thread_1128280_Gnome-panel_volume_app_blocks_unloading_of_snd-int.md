---
title: "Gnome-panel volume app blocks unloading of snd-intel8x0 in suspend"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zaomaster on 2009-04-17
So, if the gnome-panel volume app is loaded it keeps the snd-intel8x0 module from unloading at suspend, thus causing the clock to be at a different speed on wakeup. This then forces sampling errors, causing the tempo of all music/sound to be higher than normal, i.e. it sounds like the chipmunks. Any idea why this is happening/what I can do about it, other than removing the app?

---

