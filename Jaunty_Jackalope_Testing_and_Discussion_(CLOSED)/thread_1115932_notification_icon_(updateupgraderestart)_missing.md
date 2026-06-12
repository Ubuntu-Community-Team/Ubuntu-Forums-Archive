---
title: "notification icon (update/upgrade/restart) missing"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by frogotronic on 2009-04-04
Hi All,

  Running Jaunty (via WUBI on XP box).  My notification icons are missing - How do I get them back?

(I've tried all the obvious stuff via Synaptic)

- CH

---

### Post by frogotronic on 2009-04-13
> **cement_head said:**
> Hi All,

  Running Jaunty (via WUBI on XP box).  My notification icons are missing - How do I get them back?

(I've tried all the obvious stuff via Synaptic)

- CH

*bump*

---

### Post by ktp on 2009-04-13
> **cement_head said:**
> *bump*

Could it be that you are looking for the notification icon which is removed now.  

[http://ubuntuforums.org/showthread.php?t=1122292](http://ubuntuforums.org/showthread.php?t=1122292)

---

### Post by frogotronic on 2009-04-13
Hey KTP, thanks - yep, that it - changed it back

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

Also, bug report here:  [https://bugs.launchpad.net/bugs/332945](https://bugs.launchpad.net/bugs/332945)

---

### Post by ktp on 2009-04-13
Yes, the bug report...I think I said my peace...even if it when ignored.  Oh well.

---

