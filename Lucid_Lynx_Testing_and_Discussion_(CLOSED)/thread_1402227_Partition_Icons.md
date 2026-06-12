---
title: "Partition Icons"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-02-08
Since an update about 2 weeks ago the partitons on my computer ie. media and W7 do not show up on my desktop as drive icons nor at all, but are mounted and show up in the places menu. Anyone else experiencing this behavior?

---

### Post by tad1073 on 2010-02-12
bump

---

### Post by VMC on 2010-02-12
Mine are not mounted , but they do show up under "Places". Are you partitions auto-mounted? What does fstab show?

---

### Post by shafin on 2010-02-12
Press Alt-F2 and run gconf-editor. Go to Apps\Nautilus\Desktop. Check the Show Volumes key. If its unchecked, tick it.

---

### Post by tad1073 on 2010-02-12
> **shafin said:**
> Press Alt-F2 and run gconf-editor. Go to Apps\Nautilus\Desktop. Check the Show Volumes key. If its unchecked, tick it.

Thank you, that did it.

---

### Post by tad1073 on 2010-02-12
> **VMC said:**
> Mine are not mounted , but they do show up under "Places". Are you partitions auto-mounted? What does fstab show?

Yes, they are auto mounted.

---

### Post by VMC on 2010-02-12
> **shafin said:**
> Press Alt-F2 and run gconf-editor. Go to Apps\Nautilus\Desktop. Check the Show Volumes key. If its unchecked, tick it.

Your right. I mis-understood his problem. Correct, when mounted they do show up on my desktop and my volume key is set.

I thought he couldn't mount any volume.

---

