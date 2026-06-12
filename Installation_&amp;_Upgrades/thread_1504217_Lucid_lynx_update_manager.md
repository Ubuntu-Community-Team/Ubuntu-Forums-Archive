---
title: "Lucid lynx update manager"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by amalgamas on 2010-06-07
Ubuntu 10.04, update manager: the package "libmyth-perl" shows up, but is greyed.  I have purged all myth-tv (assuming this package belongs there) from my system, but I am unable to remove this package from the update manager.  Any advice?

---

### Post by SlidingHorn on 2010-06-07
may be a stupid question, but have you tried removing it in a terminal?

```
sudo apt-get remove libmyth-perl
```

If you have and it didn't work, what error message were you given?

---

### Post by amalgamas on 2010-06-08
As I still am a unexperienced (but happy) ubuntu user: not stupid at all.  It worked, thanks!

---

