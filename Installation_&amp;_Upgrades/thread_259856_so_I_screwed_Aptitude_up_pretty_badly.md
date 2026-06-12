---
title: "so I screwed Aptitude up pretty badly"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by d1sturbanc3 on 2006-09-18
I was playing around the source.list file, and  somehow I manage to  create some dependencies error. I see this red "Resolving dependicies" line when I run aptitude. I hit e, and I get open 7093 and closed 5000. Apititude now just freezes after I g. I get about 16 conflicts.

Anyway I can reset on it?

---

### Post by aysiu on 2006-09-18
Get a fresh sources.list...
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

...and try again.
```
sudo aptitude update
```

---

### Post by d1sturbanc3 on 2006-09-20
Thanks it worked

---

