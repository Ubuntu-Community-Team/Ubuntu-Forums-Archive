---
title: "linux-image-2.6.28-15 generic"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by ac03aher on 2009-12-13
I am new to Ubuntu and my general maintenance consists of running the Update Manager. I did so a few weeks ago and now I have the error message attached. How can I solve this?

---

### Post by Fafler on 2009-12-14
Try opening a terminal and type

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

If that doesn't work try

```
sudo apt-get --fix-broken install
```

---

