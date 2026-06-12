---
title: "Update problems: python-papyon, gwibber, software-center"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ljrmorgan on 2010-04-15
I just ran an upgrade (not dist-upgrade), and these packages didn't install properly:

```
Errors were encountered while processing:
 python-papyon
 gwibber
```

Plus I got this for software-center:
```
Setting up software-center (2.0) ...
Segmentation fault (core dumped)

```

Then I got loads of crash reports...

Anyone else got this? I'm on amd64

---

### Post by ljrmorgan on 2010-04-15
Seems to have fixed itself - I waited a bit and re-ran apt-get update and apt-get upgrade and they seem to be fixed now.

---

