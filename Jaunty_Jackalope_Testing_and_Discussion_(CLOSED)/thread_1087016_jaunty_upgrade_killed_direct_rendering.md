---
title: "jaunty upgrade killed direct rendering"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nocturn on 2009-03-04
I upgraded my Dell latitude D820 to Jaunty and noticed that the compiz effects where horribly slow.

After some tests it turns out that direct rendering is not enabled any more:

```
xdpyinfo |grep -i render                            (03-04 21:55)
    RENDER

```

xorg.conf is still empty as before.  This machine has intel graphics on board.

Any ideas what I can do to get it working again?

---

### Post by nocturn on 2009-03-04
Ok, I made a mistake, should have used glxinfo to check direct rendering and it is still on.

But compiz effects are dog slow now...  and I'm lost to what the cause can be.

---

