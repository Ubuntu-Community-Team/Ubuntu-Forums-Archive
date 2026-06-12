---
title: "GtkWarning while starting gedit"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by sajja on 2011-05-10
Hi,
   I upgraded from version 10.10 to 11.4. When I am trying to access the gedit tool I am getting the following warning

/usr/lib/gedit-2/plugins/GeditLaTeXPlugin/src/base/decorators.py:232: GtkWarning: IA__gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
  menu.add(gtk_action.create_menu_item())
2011-05-10 14:50:42,080 WARNING	GeditWindowDecorator - There is already a decorator for tab <gedit.Tab object at 0x2b3e140 (GeditTab at 0x2b246f0)>
2011-05-10 14:50:42,482 WARNING	GeditTabDecorator - No editor class found for extension

How to solve this.

Thanks,
Sajja

---

### Post by lechien73 on 2011-05-10
Hello & welcome to the forums :)

It could be an issue with a gedit plugin, what output do you get if you try running it from a terminal window?

```
gedit &
```

---

### Post by sajja on 2011-05-10
same thing is happening. Same warning message.

---

