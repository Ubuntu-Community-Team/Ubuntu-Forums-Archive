---
title: "SNAP not installed by default on 20.04"
date: 2021-07-02
forum: Installation &amp; Upgrades
---

### Post by techdevplus on 2021-07-02
I have a fresh install on 20.04.  However, SNAP is not installed.  How do I install manually?

---

### Post by TheFu on 2021-07-02
> **techdevplus said:**
> I have a fresh install on 20.04.  However, SNAP is not installed.  How do I install manually?

Assuming you are talking about the snapd subsystem and not the "snap" DNA sequence searcher ... 

a) you are luck!  It has installed on every 20.04 install that I've done.  
To install: **sudo apt install snapd**
To search for packages, use *sudo apt search {part of name}* ---->  **sudo apt search snap** The search will return a few things, including this:
```
snapd/focal-updates,now 2.49.2+20.04 amd64 [installed]
  Daemon and tooling that enable snap packages
```

b) It may already be installed.  Check by running **snap list**

c) Not all snaps work everywhere.  Sometimes they are overly constrained.  You'll see.

---

### Post by techdevplus on 2021-07-03
Thanks - that seems to have resolved my issue.

---

