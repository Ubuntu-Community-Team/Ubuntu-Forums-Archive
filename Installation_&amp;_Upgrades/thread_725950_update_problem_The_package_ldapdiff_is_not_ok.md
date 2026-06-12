---
title: "update problem: The package ldapdiff is not ok"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by raiwo on 2008-03-16
tried to update gutsy & now getting error 'E:The package ldapdiff is not ok and I don't know how to fix it!'

now when trying to open synaptic packet manager i get error```
E: The package ldapdiff is not ok and I don't know how to fix it!
E: Internal error opening cache (1). Please report.
```

also tried  sudo apt-get install -f but it didn't help

how to fix this?
using gutsy 32bit version

---

### Post by zvacet on 2008-03-16
```
sudo apt-get install --reinstall ldapdiff
```

---

### Post by raiwo on 2008-03-16
```
sudo apt-get install --reinstall ldapdiff
[sudo] password for XXX:
Reading package lists... Done
Segmentation fault (core dumped)

```

any solution for this?

---

### Post by Pumalite on 2008-03-16
sudo dpkg --remove --force-remove-reinstreq ldapdiff
Then reinstall

---

### Post by raiwo on 2008-03-16
found my own solution; delete .bin files from /var/cache/apt & everything works fine. Thanks anyway

---

### Post by Pumalite on 2008-03-16
Glad you got it working.

---

