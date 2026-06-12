---
title: "Is it possible to resize window list bar?"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by kartal on 2008-11-30
Hi
I want to be able to have more rows on my application list bar. I hate that when I have apps more than usual size all are resized and I cannot see their names on the bar.

thanks

---

### Post by olejorgen on 2008-11-30
IIRC you can set the size in the panel properties. (right click -> properties/preferences)

---

### Post by kartal on 2008-11-30
Hi

I cannot get to the settings you mention. I tried  clicking different places on the bar but I am not seeing anything reminiscent of that. Here is how it looks on my desktop

[IMG]http://stashbox.org/310572/bar.jpg[/IMG]

---

### Post by olejorgen on 2008-12-01
Try to remove one of the icons. (eg. firefox) and right click at the empty spot. This should get you to the panel properties.

You could also run **gconf-editor** and navigate to (search for panel) /apps/panel/toplevels/top_panel_screen0. Then double the size attribute

---

