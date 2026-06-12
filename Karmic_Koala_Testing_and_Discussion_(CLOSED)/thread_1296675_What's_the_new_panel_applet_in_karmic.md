---
title: "What's the new panel applet in karmic?"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rinoshea on 2009-10-20
Does anyone know the package wname of the new Karmic panel applet which merges IM & shutdown, log off, hibernate, & suspend options.

It's the one in the top right which displays your name and a chat icon.

I just upgraded from 9.04 and new karmic-only packages (including the new disk utility) were not installed, so I don't have access to that applet.

Any help is appreciated!

---

### Post by rinoshea on 2009-10-21
Bump?

---

### Post by hanzomon4 on 2009-10-21
fusa-applet fast user switch applet

---

### Post by 23meg on 2009-10-22
> **hanzomon4 said:**
> fusa-applet fast user switch applet

No, it's *indicator-session*. There's no such package as *fusa-applet* anyway.

---

### Post by hanzomon4 on 2009-10-22
I've seen it called fusa in bug reports and forum post in relation to the applet, and [on marky marks blog]("http://www.markshuttleworth.com/archives/233")

---

### Post by 23meg on 2009-10-22
> **hanzomon4 said:**
> I've seen it called fusa in bug reports and forum post in relation to the applet, and [on marky marks blog]("http://www.markshuttleworth.com/archives/233")

That's the old applet; indicator-session is the rewrite for the new GDM.

---

### Post by rinoshea on 2009-10-23
> **23meg said:**
> That's the old applet; indicator-session is the rewrite for the new GDM.


OK, I installed indicator-session. Now how do I enable it? There is no new applet listed and indicator-session is (not surprisingly) a valid command. Does anyone know how to get this applet working?

---

### Post by 23meg on 2009-10-23
The applet name is "Indicator Applet Session". Try restarting gnome-panel if it doesn't appear in the list.

---

