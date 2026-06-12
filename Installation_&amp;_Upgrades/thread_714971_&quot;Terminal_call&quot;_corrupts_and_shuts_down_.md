---
title: "&quot;Terminal call&quot; corrupts and shuts down system"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by mdchek on 2008-03-04
[I][B]When I select "terminal" from the menu I get VERTICAL COLOR BANDS and then the system closes out and makes me log in again.

Running Xubuntu, Intel 566, NB Video, 512 Ram

Thx in advance[/B][/I]  
: { )

---

### Post by .nedberg on 2008-03-04
Change
```
Defaultdepth    24
```
to
```
Defaultdepth    16
```

in /etc/X11/xorg.conf and restart X.

---

