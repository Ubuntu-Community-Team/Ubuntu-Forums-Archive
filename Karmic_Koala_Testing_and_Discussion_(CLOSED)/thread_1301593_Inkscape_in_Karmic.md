---
title: "Inkscape in Karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gotaserena on 2009-10-26
Hello everybody!

I'm having trouble running inkscape in my beta version of karmic (fresh install). The program opens, only to inform me that it encountered an internal error and need to close. I've cleaned the configuration files and gtk customizations, to no avail.

Is anybody else having problems?

---

### Post by ghostborg on 2009-10-26
[http://webupd8.blogspot.com/2009/09/install-inkscape-047-pre3-in-ubuntu.html]("http://webupd8.blogspot.com/2009/09/install-inkscape-047-pre3-in-ubuntu.html")

Found this - don't know if this helps or hurts.

---

### Post by vinutux on 2009-10-26
Open it from terminal... what is the output...........

---

### Post by gotaserena on 2009-10-26
Found the culprit! It's the gnome globalmenu which is making inkscape crash. I'll have to add an exception in the menu from now on...

Thanks for the answers!

---

### Post by vinutux on 2009-10-26
ok...plz...mark thread SOLVED under **[COLOR="Red"]thread tools[/COLOR]** top right........:D

---

### Post by gotaserena on 2009-10-26
[http://code.google.com/p/gnome2-globalmenu/issues/detail?id=526&q=inkscape](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=526&q=inkscape)

Seems it's solved upstream in globalmenu. Thx, everyone!

---

