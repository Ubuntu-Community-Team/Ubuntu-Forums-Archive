---
title: "Can someone confirm this bug fix within the new theme?"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xl_cheese on 2010-03-05
I don't have lynx installed yet so I can't check it out.  

Did they really implement a grabbable menubar?

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532421](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532421)

---

### Post by junior aspirin on 2010-03-05
Yep, just checked this. you can drag a window through using the bit of the menubar that has no menus.

---

### Post by shafin on 2010-03-05
> **junior aspirin said:**
> Yep, just checked this. you can drag a window through using the bit of the menubar that has no menus.
Thats great, is it for this theme only or for all themes?

---

### Post by 23meg on 2010-03-05
> **xl_cheese said:**
> Did they really implement a grabbable menubar?


[Yes]("http://kwwii.blogspot.com/2010/03/new-in-lucid.html").

---

### Post by knn on 2010-03-05
Cool, it's good to see they haven't forgotten about usability.

---

### Post by Atermoon on 2010-03-06
Too bad it only works with the default theme. It it some kid of new theme option or a setting in gtk?

---

### Post by zacbarton on 2010-03-06
> **Atermoon said:**
> Too bad it only works with the default theme. It it some kid of new theme option or a setting in gtk?

I think this might be it?

GtkMenuBar::window-dragging = 1

---

### Post by Atermoon on 2010-03-06
> **zacbarton said:**
> I think this might be it?

GtkMenuBar::window-dragging = 1

Exactly! Thanks a lot, I checked the entire gtkrc but I must have missed it somehow.

---

