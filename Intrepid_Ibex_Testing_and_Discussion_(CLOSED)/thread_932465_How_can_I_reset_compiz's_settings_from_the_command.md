---
title: "How can I reset compiz's settings from the command line?"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-09-28
Hi,

I seem to be having some problems with my laptop and compiz: activating some plugins -alpha blur, for example- corrupts the screen so it becomes impossible to work with. In case this happens again, is there anything I can do from the commandline, any configuration folder I can remove to reset compiz's settings back to default?

---

### Post by BwackNinja on 2008-09-28
They are actually gconf keys iirc, but you can always switch to metacity ```
metacity --replace
``` and then disable whatever is giving you problems in ccsm.

---

