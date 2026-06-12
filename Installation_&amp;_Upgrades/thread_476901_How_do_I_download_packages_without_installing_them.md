---
title: "How do I download packages without installing them?"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by TheForkOfJustice on 2007-06-17
Can someone tell me how to download multiple deb packages at one time from the Ubuntu repos without installing them?

Can you also tell me which directory the packages are downloaded to by default?

---

### Post by az on 2007-06-17
> **TheForkOfJustice said:**
> Can someone tell me how to download multiple deb packages at one time from the Ubuntu repos without installing them?

Can you also tell me which directory the packages are downloaded to by default?

sudo apt-get -d install foo

foo.deb will be downloaded to /var/cache/apt/archives

---

