---
title: "Howto get rid of the panels on login (lucid)"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by stobbsm on 2010-04-23
I found this solution when I finished setting up AWN the way I wanted it, and still had that stupid top bar taking up my precious screen real estate.

This is a hack, but it works, and until gnome-panel appears in Sessions again, it's all I've found that works.

Press Alt+F2 to open the run dialog (Super+space if you prefer Gnome Do).
type gconf-editor

In the window that appears, expand the following:
desktop
-session

Select session, and double click on the name "required_components_list"
Highlight panel and press remove.

Now close gconf-editor, logout and log back in.
Viola! No more gnome-panel!

---

