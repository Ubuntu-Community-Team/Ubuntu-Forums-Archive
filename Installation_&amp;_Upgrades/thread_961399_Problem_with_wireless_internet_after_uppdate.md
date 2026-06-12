---
title: "Problem with wireless internet after uppdate"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Funndinn on 2008-10-28
Hiya.

While I was uppdating with the latest stuff, I had to shut down the computer. Now it refuses to connect to the internett by wireless and I cant use the volume upp/down buttons on the keyboard.
 When I tried to run the uppdate manager, this appears:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Any idea how to proceed?

Be gentle, it's my first time

---

### Post by torswin on 2008-10-28
First open the terminal and write

```
sudo dpkg --configure -a
```

write your own password when asked.

Wait for success.

---

