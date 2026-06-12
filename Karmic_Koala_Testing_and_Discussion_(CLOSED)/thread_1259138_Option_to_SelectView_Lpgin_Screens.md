---
title: "Option to Select/View Lpgin Screens?"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-06
I thought it would be under "login screens", where was it moved?

---

### Post by Seventh Reign on 2009-09-06
Unfortunately they have not added that option to 9.10 yet.  So we are kinda stuck with the default for now.

Crossing my fingers that they are going to put it back.

---

### Post by sports fan Matt on 2009-09-06
Ok, I thought I was missing something...:lolflag:

---

### Post by Amaranth on 2009-09-06
I doubt it'll be back for 9.10 if at all. GDM is just using plain GTK+ widgets now so without a custom engine or patch to the GDM code itself the most you can do is change the color.

---

### Post by ranch hand on 2009-09-06
The background is easy to replace.

---

### Post by plun on 2009-09-06
Change GDM.....it can easily be done...

> (1) Logout to GDM, switch to a tty, Ctrl-Alt-F1, login
(2) Execute: export DISPLAY=:0.0
(3) Execute: sudo -u gdm gnome-control-center
(4) Switch back to the gdm screen (ALT-F7).
The control center should be visible.
(5) Configure you background, theme, fonts, ...

Credits stef70
[http://ubuntuforums.org/showthread.php?t=1202843&page=41](http://ubuntuforums.org/showthread.php?t=1202843&page=41)

:)

---

### Post by kestal on 2009-09-06
> **plun said:**
> Change GDM.....it can easily be done...



Credits stef70
[http://ubuntuforums.org/showthread.p...202843&page=41](http://ubuntuforums.org/showthread.p...202843&page=41)

:)

Awesome.

The correct link is [Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1202843&page=41").

For some reason yours was slightly truncated and missing a few characters.. didn't work for me.

---

### Post by rburkartjo on 2009-09-06
yes it would be nice if we would have that option when 9.10 goes final but no big deal very few problems so far with alpha5

---

### Post by Amaranth on 2009-09-06
Right, that will lets you change the colors, background, and slightly change the look but don't expect anything like what the old GDM used to be capable of.

---

