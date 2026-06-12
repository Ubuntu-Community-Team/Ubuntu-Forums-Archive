---
title: "Want to file a bug, but don't know where"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-09-24
Hi,

I guess you have noticed how the new xstart screen fades out nicely when you log in.

Sometimes the fade out happens when the user's wallpaper and desktop icons are already loaded, which results in a very pleasant effect, like saying "your computer is ready to be used".

But other times the fade happens too soon, when the wallpaper and icons haven't been loaded yet. Then those appear suddenly, without a fade or anything, and that's quite ugly.

I would like to file a bug suggesting that xstart wait until everything is ready, but I'm not sure where to do it. There seems to be no "xstart" package in Launchpad, so what can I do?

---

### Post by FuturePilot on 2009-09-24
The package you're looking for is "Xsplash"

---

### Post by Bou on 2009-09-24
D'oh, got the wrong name. Thanks dude.

---

### Post by FuturePilot on 2009-09-24
> **Bou said:**
> D'oh, got the wrong name. Thanks dude.

No problem. :) I also agree. I think it could be sticking around for a bit longer. Seems to be going away right before everything appears, icons, panel applets, etc.

---

### Post by Bou on 2009-09-24
Just filed the bug: [https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/435692](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/435692)

---

