---
title: "Deskbar broken?"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2009-03-10
I just 'upgraded' to Jaunty, forfeiting stability for awesomenss. It's already caused me to revert to Pidgin for the joy of integrated message notifications and decent IRC support, although Empathy continues to have a special place in my heart.

Anyhow, first thing I noticed was the bizarre death of Deskbar. Every time I add the applet, it crashes. Here is the command line output after running the server directly then adding it to the panel:
```
dmccall@dylan-laptop:~$ /usr/lib/deskbar-applet/deskbar-applet 03-10 08:36:02 deskbar.core.ModuleLoader WARNING  Class BeagleHandler in file /usr/lib/deskbar-applet/modules-2.20-compatible/beagle-static.py has missing requirements. Skipping.
Segmentation fault (core dumped)

```You can ignore that beagle-static module part; Deskbar crashes the same way if I remove the module.

Before I file a bug report, can anyone reproduce this?

---

