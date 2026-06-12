---
title: "Pointer speed bar does not stick on one position."
date: 2015-01-02
forum: Installation &amp; Upgrades
---

### Post by alexbb2 on 2015-01-02
In Ubuntu 14.04 I go to Settings and then MOUSE. I don't like the speed of the mouse cursor. It is too fast for my taste. So, I move that knob (?) to the left on the bar which is Pointer Speed. Then I close the window, open it up again and the knob is in the starting position before the change which is always in the middle. ON-OFF switch is irrelevant. I don't know why it is there. You move it to the rihgt (OFF), do the same thing and you will come back to the same position of the knob on that bar. I think it is a bug. - A.

---

### Post by MAFoElffen on 2015-01-02
Try the dconf editor
org > settings-daemon > mouse > double-click ...and set to speed numerically.

See if that sets it persistently.

---

