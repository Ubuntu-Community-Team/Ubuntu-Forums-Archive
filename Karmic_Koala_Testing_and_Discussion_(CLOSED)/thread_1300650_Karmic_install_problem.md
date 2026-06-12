---
title: "Karmic install problem"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cmcanulty on 2009-10-25
Yesterday I installed Karmic rc on my 2 laptops. One it did perfectly, the other went all through the upgrade and said to restart to complete it. On restart it goes to a terminal like prompt for name and password which I enter then it does nothing just another terminal prompt. Is there a way to rescue the Karmic or the Jaunty or to get it to boot? Apparently I can enter commands if there was one that would work?

---

### Post by MelDJ on 2009-10-25
try typing: sudo gdm or sudo gnome-desktop
if neither works, try startx

---

### Post by motsteve on 2009-10-25
If startx returns an error message about xorg, don't be surprised.  I'm still trying to figure out what is wrong with my xorg.conf file on this one.

---

