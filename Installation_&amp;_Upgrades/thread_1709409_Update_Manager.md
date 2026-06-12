---
title: "Update Manager"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by Howie Williams on 2011-03-18
In update manager under Distribution updates 
[COLOR="Red"]date-time libraries based on generic programming (default version) libboost-date-time-dev (Size: 2KB)[/COLOR]
Has check box on left but wont allow me to tick it. Even if I right click and select "tick all" still wont show tick.

---

### Post by plucky on 2011-03-18
> **Howie Williams said:**
> In update manager under Distribution updates 
[COLOR="Red"]date-time libraries based on generic programming (default version) libboost-date-time-dev (Size: 2KB)[/COLOR]
Has check box on left but wont allow me to tick it. Even if I right click and select "tick all" still wont show tick.

That usually means there are some unmet dependencies.

What version of Ubuntu are you using?

---

### Post by Howie Williams on 2011-03-18
Plucky, I'm running Ubuntu 10.10 Maverick

---

### Post by plucky on 2011-03-18
Just installed it on 10.10 and no problem.

You can open Synaptic Package Manager and navigate to **Custom Filters** and the select **Upgradable (Upstream)**.If it is in there,select it and mark for upgrade.


If not,wait for a day to see if the next update will remove it.


Good Luck

---

### Post by Howie Williams on 2011-03-19
Plucky, that did the trick. Thank you.

---

