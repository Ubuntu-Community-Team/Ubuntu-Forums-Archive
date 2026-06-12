---
title: "Dependencies messed up"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by grantleroux on 2007-05-01
Here's the problem:

The libstdc++6-4.1-dev package depends on g++-4.1 and that depends on libstdc++6-4.1-dev!

How am I supposed to install them?

---

### Post by renzokuken on 2007-05-01
you could try running

```
sudo apt-get -f install
```

that should fix broken dependencies

---

### Post by tmogeem on 2007-05-23
> **renzokuken said:**
> you could try running

```
sudo apt-get -f install
```

that should fix broken dependencies


i love you .. thank you very much

---

