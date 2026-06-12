---
title: "[SOLVED] lost window borders, compiz hasnt registered a window manager"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by 99bluefoxx on 2008-01-05
so after staying up all night to upgrade my ubuntu to 7.10 and finally finishing and rebooting, i seem to have lost my window decorations[borders, close, minimize/maximize controls, etc]
i tried to open gnome-window-properties but i get a dialog saying ```
 window manager 'compiz' has not registered a configuration tool
```what does this mean and how do i fix it?
EDIT: after searching around on google[i dislike but i was desperate] i found the comand ```
metacity --replace
``` which worked perfectly for me, lol
so much for this thread, hopefully it helps someone else though

---

### Post by buckykat on 2008-01-09
that's not a solution, your compiz is still broken, metacity --replace just goes back to your default wm.

---

### Post by 99bluefoxx on 2008-01-10
lol, i got it fixed up with compiz now, i took metacity --replace out of startup, put in compiz --replace once, rebooted and fiddled around under my system>preferances menues after a while hen in sys>prefs>apperance on the last tab i found that changing the "none" checkbox to "custom" got it fixed
i just had to get used to gutsy, lolz
now onto other issues, like fixing the sansa's unmount error, eternally annoying

---

