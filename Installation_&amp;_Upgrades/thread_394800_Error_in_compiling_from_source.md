---
title: "Error in compiling from source"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by padmanabh on 2007-03-27
I am having trouble in compiling anything from source...I have tried building gnome 2.18 and WINE from source ...bothend with same error:

> checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

what exactly is the problem?

---

### Post by taurus on 2007-03-27
You need to have the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by padmanabh on 2007-04-08
thanks very much.

---

