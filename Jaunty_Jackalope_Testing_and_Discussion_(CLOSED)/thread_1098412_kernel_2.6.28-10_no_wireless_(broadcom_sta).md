---
title: "kernel 2.6.28-10 no wireless (broadcom sta)"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Myxb on 2009-03-17
HI,

After last kernel update to 2.6.28-10 I lost my wireless. it seems that the package linux-restricted-modules-2.6.28-10-generic does not contain Broadcom STA driver anymore. I have BCM4328 rev 03 card.

Do they forgot to include the driver into the new kernel or I miss something here?

---

### Post by nyarnon on 2009-03-17
How did you upgrade? Under apt it is flagged here als 'holding back', meaning not all dependencies are met yet. It's not a good idea to force updates with synaptic.

---

### Post by Myxb on 2009-03-17
I think I indeed forced the installation of the package. This might be the cause of the problem. I wait on the old kernel and see what will happen after next updates.

---

