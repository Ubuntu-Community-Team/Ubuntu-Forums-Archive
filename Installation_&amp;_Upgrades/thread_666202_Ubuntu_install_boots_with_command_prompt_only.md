---
title: "Ubuntu install boots with command prompt only"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by atrius on 2008-01-13
After the PC boots I select install Ubuntu, but instead of loading thge GUI it displays only a command prompt.

Does any one now what the problem could be?

Many thanks,

Atrius.

---

### Post by berthiggins on 2008-01-13
Looks like it did not recognose your video setup correctly .
Try this code at the command window and follow the prompts


sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by berthiggins on 2008-01-13
Or you could use the instructions on this link.
Not sure what the -phigh part does in these instructions it is not used


[http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

---

