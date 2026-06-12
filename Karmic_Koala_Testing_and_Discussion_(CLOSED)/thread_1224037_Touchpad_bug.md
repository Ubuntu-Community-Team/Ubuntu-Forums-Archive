---
title: "Touchpad bug"
date: 2009-07-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Durden on 2009-07-26
Not sure how to file a bug or look to see if this is already reported. But basically, I installed Karmic on my laptop and before grabbing the latest updates (I installed from CD) my touchpad was working great. After the updates I noticed tap-to-click on my touch worked in GDM but not in Gnome. I did some digging and found the enable/disable option in the mous settings but these worked to no avail.

I solved the problem by going into gconf-editor Desktop > gnome > perhipherals. In there were two things, the "mouse" section and the "touchpad" section. I noticed the tap-to-click settings were enabling/disabling in the "mouse" section instead of the "touchpad" section as they should. So I manually enabled in the touchpad section myself.

Minor problem but seems easy enough to fix.

---

### Post by psyke83 on 2009-07-27
Thanks for the information. Keep in mind that common issues like this have probably been [discussed already]("http://ubuntuforums.org/showthread.php?t=1221888&highlight=touchpad"). The "Search this forum" link is very handy...

---

### Post by dirtylobster on 2009-07-27
Thanks! Worked like a charm.

---

