---
title: "Disable Chromium updates"
date: 2018-05-12
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2018-05-12
Ubuntu 18.04

I want to disable updates to Chromium as I don't use it, favoring Chrome Stable. Command?

---

### Post by dino99 on 2018-05-12
sudo apt purge chromium*  :D

---

### Post by TheFu on 2018-05-12
Why not just remove it?
```
sudo apt remove chromium-browser
```

---

### Post by deadflowr on 2018-05-12
> **TheFu said:**
> Why not just remove it?
```
sudo apt remove chromium-browser
```

+1 better the name is in full as you might also have the chromium-codecs packages installed and using the * will mark those for removal as well.

Might also double check that the snap version is not the installed package
```
snap list
```
will show all installed snaps.
to remove a snap just run
```
sudo snap remove <the name of the package in the list>
```

---

