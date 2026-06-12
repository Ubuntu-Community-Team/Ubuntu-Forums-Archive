---
title: "How to uninstall when not in Synaptic?"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by BomanAJeff on 2008-01-04
I downloaded a clipboard manager from it's Website, not through Synaptic.

It doesn't work, so I tried to uninstall it.Problem is it's not in Synaptic or shown in Add/Remove. How can I get rid of it?

---

### Post by taurus on 2008-01-04
How did you install it?  Was it a .deb or was it a .tar.gz (you have to build it yourself)?

```
sudo dpkg -r *program*
```

---

### Post by BomanAJeff on 2008-01-05
It was a .deb for the Desktop Data Manager (DDM).

**Update**: I got it uninstalled with the code you provided. Thanks.

---

