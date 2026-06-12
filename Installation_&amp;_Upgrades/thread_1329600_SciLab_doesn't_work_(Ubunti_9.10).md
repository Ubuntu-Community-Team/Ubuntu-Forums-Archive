---
title: "SciLab doesn't work (Ubunti 9.10)"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Rainaldo on 2009-11-17
It seems to be not possible to get SciLab 5.1.1 to work correctly on Ubuntu 9.10.

If you try to execute the demo: Simulation --> n-pendulum, you get allways an error. The error you get is not allways the same, but in the most cases you get a message with an Uicontrols-error and the hint to try 'help usecanvas'.

---

### Post by ciric50 on 2010-01-31
Actually it probably is working for the most part. The error message indicates it is in a mode where GUI controls and graphics cannot be done at the same time. If you have Scilab code that does this, add the following line to it before any graphics:

usecanvas(%F)

and it will then work correctly.

---

