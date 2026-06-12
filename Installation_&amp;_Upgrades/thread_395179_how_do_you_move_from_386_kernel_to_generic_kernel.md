---
title: "how do you move from 386 kernel to generic kernel?"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by Slapyo on 2007-03-27
so when i initially installed the nvidia drivers it had me install the 386 kernel.  i was under the impression that i had to use that to use the nvidia drivers.  i've since found out that i can use the generic kernel.  so my question is this, how do i install the nvidia drivers on the generic kernel.  once i do that, i would boot onto that kernel.  then how would i remove the 386 kernel so i don't have to see it in the boot list anymore and so updates to it won't come through since i won't be using it anymore.  newbie here.

thanks.

---

### Post by Slapyo on 2007-03-28
by running the following command in a terminal window while on the 386 kernel, this did the trick.

```
sudo apt-get install linux-generic
```

it went through and did it's thing.  then i booted into the generic kernel no problem.  everything is working great.

now i just need to remove the 386 kernel.

---

### Post by dcstar on 2007-03-29
> **Slapyo said:**
> by running the following command in a terminal window while on the 386 kernel, this did the trick.

```
sudo apt-get install linux-generic
```

it went through and did it's thing.  then i booted into the generic kernel no problem.  everything is working great.

now i just need to remove the 386 kernel.

All of these things can be done via Synaptic.

---

### Post by Slapyo on 2007-03-30
i'm guessing i would just look for linux-generic in synaptic then?

---

