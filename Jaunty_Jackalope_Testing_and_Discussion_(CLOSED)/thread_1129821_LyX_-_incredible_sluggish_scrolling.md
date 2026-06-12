---
title: "LyX - incredible sluggish scrolling"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Jingo on 2009-04-19
I just installed Jaunty last night, and as part of it, LyX 1.6.2 from the repos.

LyX seems incredible sluggish while scrolling.
While scrolling in LyX, xorg uses 99% cpu !

Anyone else experiencing this? Any known cause?

Edit: I have compiz disabled!

---

### Post by Jingo on 2009-04-19
Found this to be caused by the radeon driver using exa acceleration.

Switching to xaa acceleration solved this!

---

