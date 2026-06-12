---
title: "Gnome-settings-daemon"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by COLiNx86 on 2009-03-07
gnome-settings-daemon won't load anymore. I just recently installed jaunty and did an upgrade, and installed flash, codecs, and all that kind of stuff. I think I may have installed some fonts as well though.  But no when I restart it won't load. and if i run gnome-settings-daemon in the terminal I get 
```
Fontconfig error: "/etc/fonts/conf.d/30-defoma.conf", line 1: no element found
```
Does anyone know how I can fix this? 
BTW: I did search but i couldn't find anyone with this problem.

---

### Post by ronacc on 2009-03-07
on my system /etc/fonts/conf.d/30-defoma.conf is a link to /var/lib/defoma/fontconfig.d/fonts.conf.

---

### Post by COLiNx86 on 2009-03-07
> **ronacc said:**
> on my system /etc/fonts/conf.d/30-defoma.conf is a link to /var/lib/defoma/fontconfig.d/fonts.conf.
Yeah mine's empty, so can you post everything yours has.

---

### Post by ronacc on 2009-03-07
first try  ```
sudo dpkg --configure -a 
``` to see if that fixes it . I may have different fonts than you so my fonts.conf wouldn't be right for you.

---

