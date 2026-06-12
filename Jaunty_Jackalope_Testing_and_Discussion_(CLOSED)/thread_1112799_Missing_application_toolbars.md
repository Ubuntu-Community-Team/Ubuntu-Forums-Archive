---
title: "Missing application toolbars"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by killersnowgoon on 2009-04-01
After a recent update, all my application toolbars (except for firefox, for some strange reason) are gone. for clarifications sake, I mean the bar at the top with File, Edit, View, etc, not the gnome panel. 
anyone have any idea as to was has caused this/how to fix it?

---

### Post by killersnowgoon on 2009-04-01
by the way, it affects both root and regular accounts.

---

### Post by killersnowgoon on 2009-04-05
anyone else having this problem/know how to fix it? its getting pretty annoying

---

### Post by taavikko on 2009-04-05
> **killersnowgoon said:**
> anyone else having this problem/know how to fix it? its getting pretty annoying

The issue is metacity/compiz related, try to disable compiz
and see if that helps.

To test 
```
metacity --replace &
```
this doesn't disable compiz.

---

### Post by killersnowgoon on 2009-04-05
it didnt work =/
thanks anyways though

---

### Post by killersnowgoon on 2009-04-07
FIXED IT! turns out i had installed globalmenu (package name gnome-globalmenu) and completely forgot about it. hope this helps someone else.

---

