---
title: "[SOLVED] 8.10 upgrade not available through update manager"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by headflux on 2008-11-06
Hi,

With previous releases of Ubuntu, update manager has automatically notified me that the release is available.  However, with 8.10, it does not appear in update manager, even if I tell it to check for updates.  I'd rather not do a clean install, so can anyone advise?

Thanks

---

### Post by Partyboi2 on 2008-11-06
Open up Software Sources and click on the "Updates" tab and change "Show new distribution release" to "Normal releases"    if not already done so. Then start update manager. If the option to upgrade still does not appear then open a terminal and try this
```
gksu "update-manager -c -d"
```

---

### Post by headflux on 2008-11-06
Great!  That did the trick.

Much Appreciated.

---

### Post by PhantoMEngineeR on 2009-04-26
Hey,
I had trouble updating as well but this time from 8.10 to 9.04. Upgrade does not appear on update manager no matter how many times I pressed the check button. Previously though, the update appeared. Somehow, it kinda disappeared suddenly. The above command did the trick for me.
Thanks!!!

---

### Post by wb0eq on 2009-04-26
Am running 8.04.  Upgrade manager only shows "8.10", after following your directions, not "9.04"  What to do?  Thanx!

---

### Post by Partyboi2 on 2009-04-26
> **wb0eq said:**
> Am running 8.04.  Upgrade manager only shows "8.10", after following your directions, not "9.04"  What to do?  Thanx!
You cannot skip releases when upgrading so you would need to upgrade to 8.10 first then onto 9.04

---

