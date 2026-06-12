---
title: "Nvidia in restricted driver manager"
date: 2008-08-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sddfdds on 2008-08-07
Im using 177 with a 6800.  It seems to mostly be working (except for the freakout/crash upon startup and the fallback to metacity, followed by a compiz --replace to make effects work) but in the restricted drivers manager, it says "No proprietary drivers are in use on this system"  Is this a benign problem or a sign of something more serious being wrong?

---

### Post by RAOF on 2008-08-07
Benign.  You probably don't have the various nvidia-xxx-modaliases packages installed; they're what Jockey (the restricted drivers manager) uses to determine what drivers support your card.

---

