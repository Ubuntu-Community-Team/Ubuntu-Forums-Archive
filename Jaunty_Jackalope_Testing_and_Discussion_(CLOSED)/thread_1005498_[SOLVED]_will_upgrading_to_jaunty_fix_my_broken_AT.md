---
title: "[SOLVED] will upgrading to jaunty fix my broken ATI x1300 drivers?"
date: 2008-12-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-12-08
last week it was working fine. Today I noticed it was not working.
no compiz, no googleearth, no glxgears, no games work

it claims the driver needs to be activated but never will activate when I try.


SOLVED by reinstalling all FGLRX packages in synaptic

---

### Post by DavidMIRV on 2009-01-15
same problem here.. and the non-restricted/OSS drivers in Jaunty seem to run like crud!  Let me know if you fix this!  Had the problem for awhile where the ati restricted driver will run 2 xserver processes therefore defeating performance.

---

### Post by Mazza558 on 2009-01-15
> **DavidMIRV said:**
> same problem here.. and the non-restricted/OSS drivers in Jaunty seem to run like crud!  Let me know if you fix this!  Had the problem for awhile where the ati restricted driver will run 2 xserver processes therefore defeating performance.

Did they run fine in Ibex before? If so, change the device options in Xorg back to "XAA" from "EXA". Some people find XAA is faster (not me though).

---

