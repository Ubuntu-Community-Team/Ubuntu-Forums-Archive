---
title: "Trouble with Update Manager"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by ODLogan on 2008-05-17
Two things:
First of all, I uninstalled transmission due to personal preference, but update manager still prompts me to update it.
Secondly, when I tried to get some other updates, I got the following message:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

---

### Post by kellemes on 2008-05-17
> **ODLogan said:**
> Two things:
First of all, I uninstalled transmission due to personal preference, but update manager still prompts me to update it.
Secondly, when I tried to get some other updates, I got the following message:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

From terminal window..
```
sudo dpkg --configure -a
```

---

### Post by ODLogan on 2008-05-17
Obviously, but what do I do from there?

---

