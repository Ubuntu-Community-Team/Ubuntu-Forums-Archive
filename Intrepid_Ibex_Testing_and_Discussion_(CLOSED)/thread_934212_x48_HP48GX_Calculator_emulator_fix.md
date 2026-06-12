---
title: "x48 HP48GX Calculator emulator fix"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jove on 2008-09-30
Intrepid borked one of my essential tools: the x48 HP48GX emulator ([http://x48.berlios.de/](http://x48.berlios.de/)) which I've been using on Linux since 1998. Screen display was horribly corrupted, probably due to some X library updates. Anyway, after a bit of digging and trial and error I noticed that if you start it with "x48 +xshm" it's all good. Hope this helps out someone else.

---

