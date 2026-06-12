---
title: "Update Manager Issues"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by crisnoh on 2007-10-19
I'm attempting to install system updates and getting the following error from Update Manager:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I'm getting a similar error when trying to upgrade to Gibbon.

---

### Post by kanna1620 on 2008-05-03
Just remove the lock file, and start your update manager or synaptic.

```
sudo rm /var/cache/apt/archives/lock
```

and you are done.

---

