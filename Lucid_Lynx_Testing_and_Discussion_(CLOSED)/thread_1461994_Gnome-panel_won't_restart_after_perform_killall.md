---
title: "Gnome-panel won't restart after perform killall"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Chromagnum on 2010-04-25
I can kill nautilus and it will restart back again, but it won't do for gnome-panel. Is it a bug in Lucid or is it just me?

I can call it back in terminal, but if I close terminal then gnome-panel also close. Temporary solution for me instead of reboot (if I accidentally kill gnome-panel) would be, call it back in terminal and then switch user or log out, and log in back again.

---

### Post by tokyobadger on 2010-04-25
```
gnome-panel &
```
should leave the panel working even if you close the terminal

---

### Post by renkinjutsu on 2010-04-25
or Alt+F2

---

### Post by Cenotaph on 2010-04-25
alt+f2 depends on gnome-panel so if the panel isnt running it wont work.

open gconf-editor

and try to see if desktop -> gnome -> session -> required_components_list includes the panel and if so, if its properly set to gnome-panel in desktop -> gnome -> session -> required_components -> panel

---

### Post by Chromagnum on 2010-04-25
@tokyobadger
Thanks, it works.

@Cenotaph
Everything set properly in gconf-editor. Is there anyway to fix it, so it will automatically restart if I kill it?

---

