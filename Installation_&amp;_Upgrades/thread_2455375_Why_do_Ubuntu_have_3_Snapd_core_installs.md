---
title: "Why do Ubuntu have 3 Snapd core installs?"
date: 2020-12-18
forum: Installation &amp; Upgrades
---

### Post by kaeksen on 2020-12-18
These are the versions on my ubuntu 20.10 fresh install.

1. Core Version: (16-2.48)
2. Core 18 Version: (20201210)
3. Core 20 Version: (20201210)

Is it suppose to be this many version in 1 fresh ubuntu install?

---

### Post by TheFu on 2020-12-18
Because the default is to keep 3 versions of every snap.  You can change that to be 2, but you cannot make it just 1.  The Snap team decided that wasting your storage and updating snaps whenever they like is "good for us."

You don't have to use any snaps and you can remove the snap subsystem, if you like.
You can setup an automatic cronjob to remove extra snaps daily, weekly, monthly, if you like.

---

### Post by CatKiller on 2020-12-18
Snaps are containerised applications, isolated from the rest of the system. They could include every single library that they need to run in every single snap, but that would have a lot of duplication. So instead they have a snap that contains common libraries, that each snap application can communicate with. There's more than one so that applications that target Ubuntu 18.04, and applications that target Ubuntu 20.04, will work on any distribution.

---

### Post by TheFu on 2020-12-18
> **CatKiller said:**
> There's more than one so that applications that target Ubuntu 18.04, and applications that target Ubuntu 20.04, will work on any distribution.

In theory. Not in reality.

---

