---
title: "fbsplash overwritten during boot"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by ehula on 2007-01-11
I installed fbsplash and it is working somewhat, but I am having the following problem. During boot, the fbsplash splash image is displayed properly while it is loading the kernel, but once it gets to a certain point, it begins to overwrite text on the splash image.

The first text to appear is:

* Activating swap...
* Checking root file system ...
and so on ...
...

I am running Edgy. Any ideas how to prevent text from writing on top of the splash image?

---

### Post by ehula on 2007-01-18
Bump...

---

### Post by ehula on 2007-01-23
> **ehula said:**
> During boot, the fbsplash splash image is displayed properly while it is loading the kernel, but once it gets to a certain point, it begins to overwrite text on the splash image.

The first text to appear is:

* Activating swap...
* Checking root file system ...
and so on ...
...


I have solved my problem! Change the following kernel parameter from:
```
splash=silent,theme:Ubuntu quiet CONSOLE=/dev/tty1
```
to
```
splash=silent,kdgraphics,theme:Ubuntu quiet CONSOLE=/dev/tty1
```

---

