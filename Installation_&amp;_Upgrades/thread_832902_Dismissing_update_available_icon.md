---
title: "Dismissing update available icon"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by hoborocket on 2008-06-18
Is there any way to rig the update notifier to ignore a certain package(s)? I have one, with dependencies, that I never intend to install, but I can't get the update icon to bugger off.

The program in question is held, but it still shows up, just unchecked, and all its unmet dependencies are there too.

I tried to rig a dummy DEB of gaim to have a higher version than the replacement package, but these things are beyond me.

---

### Post by dstew on 2008-06-18
Maybe if you remove and purge the offending package the updater will back off. You can try```
sudo apt-get remove --purge *<package_name>*
```

EDIT: Maybe I misunderstood. Is it that you want to keep a particular package without upgrading it? If so, you can try```
sudo apt-get install --no-upgrade *<package_name>*
```

---

### Post by iheartubuntu on 2008-06-18
Im still no Ubuntu pro, but couldnt you go into synaptic package manager and LOCK a specific program so it never updates?

---

