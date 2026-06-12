---
title: "APT::Default-Release error"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by phorechuk on 2012-10-11
E: The value 'lucid' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

I've been running precise for about 3 months now on x_64. As per above, I upgraded directly from lucid to precise. Most things work as expected. However, whenever I run the Synaptic Package Manager, I get the above error and it closes.

Where is this variable being set?

---

### Post by zvacet on 2012-10-12
```
gksudo gedit /etc/apt/sources.list
```

and put output here.

---

