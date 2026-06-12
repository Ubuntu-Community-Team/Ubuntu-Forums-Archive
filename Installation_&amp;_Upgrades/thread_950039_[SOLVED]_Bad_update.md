---
title: "[SOLVED] Bad update"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by driven1 on 2008-10-16
I was installing the latest updates when the update manager suddenly quit. Now, I can't get it to run at all. I tried to run 
```
sudo apt-get install -f
```
but after reading the package lists it comes back with 
```
segmentation tree faulty...50%
```

Anyone what I should do to fix this?

---

### Post by Partyboi2 on 2008-10-16
Try removing or moving out of the way the /var/cache/apt/*.bin files then run
sudo apt-get update afterwards, this should regenerate the files.

---

### Post by driven1 on 2008-10-16
worked like a charm. Any effects from removing those files permanently?

---

### Post by Partyboi2 on 2008-10-16
I don't think there will be any problems removing them. I haven't encountered any. You can always keep them for awhile and delete them at a later date.

---

