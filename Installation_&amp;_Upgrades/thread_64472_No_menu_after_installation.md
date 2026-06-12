---
title: "No menu after installation"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by nEXzEr on 2005-09-11
Well I do have a menu but it's not working, I can't see the clock or any icons at the top left corner, however I can see the Applications, Places, System but they are not working, they won't respond when I click on them and this happend when I first installed Ubuntu 5.04 AMD64. Does anyone have any idea how to fix this??

---

### Post by heimo on 2005-09-11
I'm using Breezy Badger, so some of details may be wrong. But this is what I'd try: Right click on that panel, choose 'Delete this panel', right click on lower panel, choose 'New Panel', right click on new panel and 'Add to Panel', add menubar, clock, volume manager and what ever you want on that panel. Does that work?

---

### Post by nEXzEr on 2005-09-11
the problem is I can't right click on it.

---

### Post by heimo on 2005-09-11
[QUOTE=nEXzEr]the problem is I can't right click on it.[/QUOTE]

Press CTRL+F2, enter 'xterm' [Run], type in terminal window:  ```
killall gnome-panel
```
This should restart all gnome-panels. Do you get any errors, do they respond after restart? Are both lower and top panels "dead"?

---

### Post by nEXzEr on 2005-09-11
i've tried that aswell, didn't work, it's the same.

---

### Post by nEXzEr on 2005-09-11
Okay I tried some things and solved it, all I had to do was to remove the gnome panel and then installed it again, worked like a charm (it didn't work with just re-installing it)

---

### Post by heimo on 2005-09-11
Great! :)

---

