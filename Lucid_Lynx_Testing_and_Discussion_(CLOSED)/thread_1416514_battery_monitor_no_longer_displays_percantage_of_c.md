---
title: "battery monitor no longer displays percantage of charge left"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by biomedtech on 2010-02-26
Eee PC 901, running the UNR version, dated Feb 24.3

It worked in Alpha 2, seems broken in Alpha 3.  I tried re-installing, 

"sudo apt-get install --reinstall gnome-power-manager"


But it did not restore the % of charge left.  I don't know if this is a bug, or if someone made the decision to give us less information about the remaining-time available on battery power.

---

### Post by david_ on 2010-02-26
gnome-power-manager is now using an application indicator.

Afaik application indicators doesn't support tooltips (yet) :(

---

### Post by biomedtech on 2010-02-28
Thank you for that info. I grew so accustomed to that indicator that I'd catch myself looking for it.

---

