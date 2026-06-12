---
title: "updated cups, printers are gone"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2008-01-17
I recently got some automatic updates for 7.10 including several cups related updates.  Now my system has no installed printers.  Has anyone else had the same problem, if so is there a way to find and reinstall the printers I had prior to the updated without doing them all manually?

Thanks

Jim

---

### Post by jamaas on 2008-01-17
Sorry, should have thought of this .... used synaptic to reinstall cups and it seems to work fine again.

Jim

---

### Post by erginemr on 2008-01-17
FYI for future reference, you may also use the Web interface of Cups to install/remove/view your printer(s) by entering
```
http://localhost:631
```
to your Firefox address bar.

---

### Post by Mayfoev on 2008-01-17
**This post could be related to an Ubuntu bug filed at**: [http://launchpad.net/bugs/183652](http://launchpad.net/bugs/183652) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The bug experienced by jamaas is bug 183652, caused by a regression provoked by the fix of avahi problems with CUPS. A new package of avahi is available.

---

