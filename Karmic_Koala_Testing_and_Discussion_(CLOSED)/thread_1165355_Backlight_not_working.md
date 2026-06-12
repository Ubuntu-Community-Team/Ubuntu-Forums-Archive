---
title: "Backlight not working"
date: 2009-05-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2009-05-20
For the last week or so Ubuntu seems to have forgotten that my laptop has a backlight. Is anyone else having extremely dark display issues?

---

### Post by freeman2000 on 2009-05-21
No problems on my laptop.  Are you sure the backlight isn't going out? They're not that expensive.  Good luck.

---

### Post by tensop on 2009-05-21
Happens to me on 2.6.30-rc* kernels. reverting to a 2.6.28/29 fixes the issue - however xrandr --output LVDS --set BACKLIGHT_CONTROL native
has to be used to fix erratic controls of backlight

---

### Post by macroshaft on 2009-05-21
It's ok, it came back eventually. I guess something caught up with something else.

---

