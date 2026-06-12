---
title: "gdm's new user-switch-applet in the upper-right corner doesn't theme properly"
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-07-13
Unless you are using the Human theme, the color and/or gradient will sometimes be a few shades off.

I provide Shiki-Wise and Dark Room as examples.

---

### Post by tad1073 on 2009-07-13
how do you apply themes?

---

### Post by psyke83 on 2009-07-13
> **Starks said:**
> Unless you are using the Human theme, the color and/or gradient will sometimes be a few shades off.

I provide Shiki-Wise and Dark Room as examples.

I'll take a look at it - a workaround can probably be applied to the themes, but it's possible that the panel theming logic is also flawed in these themes, so we'll see.

---

### Post by psyke83 on 2009-07-13
Ok, the problem is varied for each theme.

Human (with the 0.29ubuntu1 update in Ken's PPA) doesn't exhibit the bug (as I removed several hacks from the code to avoid inconsistencies like this).
DarkRoom still exhibits this bug as I haven't gotten around to updating this theme yet - I will soon.

Shiki-* has this problem because it hardcodes the colour of the normal background of menubars (line 251 of Shiki-Brave, for example). Filed as [Issue #99]("http://code.google.com/p/gnome-colors/issues/detail?id=99").

Starks, what other themes exhibit this problem?

---

### Post by perfectska04 on 2009-07-13
This is fixed in SVN for Shiki-Colors.

It just happens that applets will not use the pixmap background unless the resource class is matched - I fixed it by adding a new panel matching "gdm-user-switch" instead of "fast-user-switch".

Shiki-Colors has one of the most complete panel matching codes, it just needs a tweak every once in a while - as there's no GTK matching to make all panel applet resource classes work without breaking other stuff.

Edit: I mean for hybrid themes (i.e. light themes with dark panels or viceversa). Normal themes that are all dark or all light don't usually have any panel matching issues as the same background is used for almost all widgets.

---

### Post by psyke83 on 2009-07-13
> **perfectska04 said:**
> This is fixed in SVN for Shiki-Colors.

It just happens that applets will not use the pixmap background unless the resource class is matched - I fixed it by adding a new panel matching "gdm-user-switch" instead of "fast-user-switch".

Shiki-Colors has one of the most complete panel matching codes, it just needs a tweak every once in a while - as there's no GTK matching to make all panel applet resource classes work without breaking other stuff.

Thanks for the clarification. The Human theme doesn't use pixmaps for the panel, so it wouldn't exhibit this bug. I'll be sure to update the gdm-user-switch widget definition anyway.

---

### Post by perfectska04 on 2009-07-13
No problem :)

Just be sure you leave the "fast-user-switch" matching in your themes as well, for Jaunty/Hardy users.

---

