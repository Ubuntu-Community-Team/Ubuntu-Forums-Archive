---
title: "Keep getting false System Update notifications"
date: 2014-11-28
forum: Installation &amp; Upgrades
---

### Post by aaronschillings on 2014-11-28
For the past 3 hours or so I get a "System Update Available" notification in my tool bar.  When I open up my Konsole and type apt-get update, in a root shell, no updates are found.  I've also done apt-get upgrade and apt-get dist-upgrade and am still coming up empty.  Any one that has any input/advice would be much appreciated!

---

### Post by slickymaster on 2014-11-28
> **aaronschillings said:**
> For the past 3 hours or so I get a "System Update Available" notification in my tool bar.  When I open up my Konsole and type apt-get update, in a root shell, no updates are found.  I've also done apt-get upgrade and apt-get dist-upgrade and am still coming up empty.  Any one that has any input/advice would be much appreciated!

Try this at a terminal window, to see what might be hided:```
/usr/lib/update-notifier/apt-check --human-readable
```

---

