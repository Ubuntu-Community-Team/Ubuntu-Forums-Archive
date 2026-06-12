---
title: "internal error"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by witblits1970 on 2013-02-02
i ahve just upgraded to 12.12 and as normal,at least since the 12* series i have this flaming annoying message that pops up saying internal error blah blah blah. if ubuntu wants MS user to convert than these silly issues need addresing, see attachment. it makes me want to use some other distro out there. what has gone wrong recently with ubuntu> there was no such issue in the 10* or possibly the 11* series.

just for consideration

---

### Post by srekcahrai on 2013-02-02
```

sudo gedit /etc/default/apport


```

Change

```

enabled=1

```

to

```

enabled=0

```

---

