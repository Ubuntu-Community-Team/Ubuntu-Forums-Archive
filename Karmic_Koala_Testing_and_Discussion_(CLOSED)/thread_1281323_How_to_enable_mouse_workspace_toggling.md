---
title: "How to enable mouse workspace toggling?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ikisham on 2009-10-03
I'm using nVidia 185 driver and have desktop effects on normal but I have to click on the workspace icon in the panel to switch them. Even with desktop effects disabled (before the driver was installed) I could switch with the mouse wheel (over the workspace icon, not directly over the desktop).
I tried to find some relevant setting to change in gconf-editor but couldn't figure any.

---

### Post by ikisham on 2009-10-03
Have no clue how to solve it yet but I found out that no matter how much workspaces are enabled in Workspace Switcher (the panel applet) all show off as > Current workspace: "Desk 1"

---

### Post by shafin on 2009-10-03
[http://ubuntuforums.org/showthread.php?t=1276516](http://ubuntuforums.org/showthread.php?t=1276516)

---

### Post by ikisham on 2009-10-03
Thanks shafin, that solved it.

Just as an extra info, in gconf-editor that is located under apps>compiz>plugins>vpswitch>allscreens>options, next_button must be set to Button4 and prev_button to Button5

---

