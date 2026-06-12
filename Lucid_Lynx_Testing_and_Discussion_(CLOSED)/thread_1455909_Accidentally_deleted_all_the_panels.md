---
title: "Accidentally deleted all the panels"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by adit on 2010-04-16
I am using ubuntu 10.04 beta 2.  I accidentally deleted all the panels.  Now I see the desktop background filling the entire screen.  I want to bring at least one panel into view.
This never happened with previous stable releases of ubuntu.  It is impossible to delete the last panel because if I right-click the last panel there will not be any menu item called "delete this panel".

---

### Post by Sub101 on 2010-04-16
It may well not work but does running

```
gnome-panel
```

work, or does it say it is already running?

Strangely on my Beta the delete panel on the last panel IS greyed out.

---

### Post by sisco311 on 2010-04-16
> **Sub101 said:**
> It may well not work but does running

```
gnome-panel
```

work, or does it say it is already running?

Strangely on my Beta the delete panel on the last panel IS greyed out.

+1, it's grayed out for me too. 


if the panel is running & you still can't see it try to restore the default ones:

```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

---

### Post by adit on 2010-04-16
This code worked.
> gconftool-2 --recursive-unset /apps/panel
killall gnome-panelActually the panels were filled with same background color as desktop.  So they were not visible

---

### Post by sisco311 on 2010-04-16
Cool!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

