---
title: "How to fix USB drives not mounting? (libgdu problem)"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2010-03-15
I'm really obsessed by the problem of using USB storage devices.
Now I have to use mount manually, because the auto-mount software crashes at gnome startup:
```
libgdu:ERROR:gdu-pool.c:2369:device_recurse: assertion failed: (depth < 100)
```

There's a bug opened since few months, but didn't gain enough attention.
Am I the only one with this problem?

---

### Post by polki@mac.com on 2010-03-18
Nope, not alone, unfortunately. And I mean that in a nice way :-)

---

### Post by go2dell on 2010-03-18
If you found a bug report that matches your problem, please be sure to click "This bug affects (number) people.  Does this bug affect you?" at the top of the bug report.  Also, you may wish to click "Subscribe" so that you can be notified of updates to the bug report and add any information you have that may be helpful.

---

### Post by Herman on 2010-03-18
Me too ...

---

### Post by LADmaticCA on 2010-03-18
Did you check to make sure gnome-disk-utility is upgraded? I was having an automount problem and upgrading it from synaptic, plus a restart, fixed it for me.

---

