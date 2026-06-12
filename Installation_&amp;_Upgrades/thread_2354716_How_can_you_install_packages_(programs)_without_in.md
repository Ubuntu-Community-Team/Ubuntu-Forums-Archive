---
title: "How can you install packages (programs) without internet on Ubuntu?"
date: 2017-03-05
forum: Installation &amp; Upgrades
---

### Post by ahawkua on 2017-03-05
How can you install packages (programs) without internet on Ubuntu?

---

### Post by howefield on 2017-03-05
Download them from a computer that does have internet access and copy over to..

```
/var/cache/apt/archives/
```

You'd need to make sure that any dependencies or recommends that you might require were also available and install in the usual way, the package manager will find the packages copied over.

---

