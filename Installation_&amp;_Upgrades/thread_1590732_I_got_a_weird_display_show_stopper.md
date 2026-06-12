---
title: "I got a weird display show stopper"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by ak123 on 2010-10-08
i just upgraded from lucid to the maverick RC with > update-manager -dand guess what... My displays doing all sorts of weird stuff.. at boot, im shown a message saying > modprobe : FATAL: could not load /lib/modules/2.6.35-322-generic/modules.dep

Then, it resumes to a black screen..
then the mouse shows up..
then, occasionally a white square at the top left corner..
then wallpaper loads,
then it just starts reloading once the network manager password dialog shows and each time it reloads, the box moves downwards..

anyone got this problem? anyone know how to fix it? really... i should have learned my lesson by now never to system upgrade and just do clean install.

P.S. no window borders can be seen

---

### Post by dino99 on 2010-10-08
remove xorg.conf using a console:

sudo rm -f /etc/X11/xorg.conf

---

### Post by ak123 on 2010-10-08
how am i supposed to do that?? the jumping windows are all thats showing... no sign of the panel or unity..

---

### Post by ak123 on 2010-10-08
hey i figured it out... Ctrl+Alt+F1.... then login

no luck.. just the same..

---

### Post by ak123 on 2010-10-08
anyone got any help/experienced the same?? its happened at the perfect time because my desktop is now at the repair shop for ram issues...

---

### Post by ak123 on 2010-10-08
bump

---

