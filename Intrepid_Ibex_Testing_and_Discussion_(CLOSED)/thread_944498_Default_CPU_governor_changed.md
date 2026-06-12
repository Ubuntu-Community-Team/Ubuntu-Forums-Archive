---
title: "Default CPU governor changed"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TheBigT on 2008-10-11
In 8.04 by default the CPU frequency scaling was enabled, so my Core2Duo would go down to 1.6 GHz when I wasn't using it. In 8.10 the "Performance" governor is selected and the CPU is stuck at 2.4 GHz. Even if I manually switch to the "OnDemand" governor, the setting isn't retained for the next session (and the applet only sets one of the CPUs anyway, not both :( ).

My suggestions:
1. make the OnDemand governor default
2. add a mechanism so the cpu-frequency-applet retains any user selections to the next session
3. change the cpu-frequency applet so it monitors all CPUs at once (I definitely wouldn't want to have 8 of those things on a high-end PC)

---

### Post by aethralis on 2008-10-11
Is it connected to this bug -> [https://bugs.launchpad.net/linux/+bug/31291](https://bugs.launchpad.net/linux/+bug/31291) or this one [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/132403](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/132403) ?

I think it would help if you file a bug.

---

### Post by TheBigT on 2008-10-11
I don't think either of these bugs are related. If I manually change the governor, things are fine until the next restart. I will file a bug.

---

### Post by chewearn on 2008-10-25
> **TheBigT said:**
> I don't think either of these bugs are related. If I manually change the governor, things are fine until the next restart. I will file a bug.

hi TheBigT,
Where is the bug you are going to file?  I can't find it.

I am also trying to set a default governor that is not ondemand, and I think we need a simpler way to do this in Intrepid.

---

