---
title: "closing apps in avant-window-navigator problem"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by y2kss66 on 2007-10-08
ok i am in ubuntu gutsy gibbons and i have installed avant-window-navigator using this tut [http://phorolinux.com/how-to-install-avant-window-navigator-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-avant-window-navigator-on-ubuntu-710-gutsy-gibbon.html)
everything worked like a charm except when an application is open and i close it the icon doesn't go away in avant and avant changes its name to "no name" how can i fix this annoying problem because before long i have a huge desktop bar filled with worthless iicons

---

### Post by y2kss66 on 2007-10-11
any1 at all have any ideas?

---

### Post by cyberia81 on 2007-10-29
I'm having the same issue. Even after I close a program the icon remains on the dock. They display "No Name" when I hover over them. I can't right click and close them. The dock just keeps expanding further and further until it ends up off of the screen. Any ideas? Thanks!!

---

### Post by cyberia81 on 2007-10-29
Try this in terminal, worked for me:

gconftool-2 --recursive-unset /apps/avant-window-navigator

---

