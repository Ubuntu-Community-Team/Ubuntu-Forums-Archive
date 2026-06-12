---
title: "[SOLVED] Tracker running. Cannot stop it auto-starting"
date: 2008-08-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-08-10
About a week ago (ish), Tracker appeared in the notification area. Although I can exit Tracker, it always starts up at login. I've unchecked it in Sessions, but it still auto starts.

---

### Post by philinux on 2008-08-10
system>prefs>search and indexing

Turn it off there

---

### Post by pressureman on 2008-08-10
For me, trackerd was still running, even after disabling.

A brutal, but effective workaround:

```

sudo chmod -x /usr/bin/trackerd

```

---

### Post by taavikko on 2008-08-10
More permanent solution :)
```
sudo apt-get --purge remove tracker
```
who really needs indexing of files?:lolflag:

---

### Post by Gina on 2008-08-10
I don't! :)

---

### Post by phenest on 2008-08-10
Ok. So disabling worked for me. Thanks. But why did it start working in the first place?

---

