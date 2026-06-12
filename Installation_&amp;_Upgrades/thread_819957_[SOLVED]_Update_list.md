---
title: "[SOLVED] Update list"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by Valsodar on 2008-06-05
Ok, so I was wondering where does Ubuntu store/cache the list of updates.
 
now let me explain my situation:
All I wanted was to install firefox-3.0RC1 so I enabled the proposed-updates (update manager told me there are 67-ish new updates which I ignored) then I updated firefox to RC1 and disabled the proposed-updates. However update manager still tells me there are 67 new updates. How do I remove these updates form the queue? As in I want to only update when they become available normally (not proposed)

---

### Post by iaculallad on 2008-06-05
> **Valsodar said:**
> Ok, so I was wondering where does Ubuntu store/cache the list of updates.
 
now let me explain my situation:
All I wanted was to install firefox-3.0RC1 so I enabled the proposed-updates (update manager told me there are 67-ish new updates which I ignored) then I updated firefox to RC1 and disabled the proposed-updates. However update manager still tells me there are 67 new updates. How do I remove these updates form the queue? As in I want to only update when they become available normally (not proposed)

Issue the command to clean your cache:

```
sudo apt-get clean
```

Or browse the package by going to the directory:

> /var/cache/apt/archives

---

### Post by Valsodar on 2008-06-05
Thanks,

actually I did the second and still was getting that, then I remembered that thats because I set up to update every week, so the 67 updates are actually not proposed.

Silly me, but yes both methods work and I suggest using "sudo apt-get clean"

---

### Post by iaculallad on 2008-06-05
> **Valsodar said:**
> Thanks,

actually I did the second and still was getting that, then I remembered that thats because I set up to update every week, so the 67 updates are actually not proposed.

Silly me, but yes both methods work and I suggest using "sudo apt-get clean"

Yes, "sudo apt-get clean" would remove/delete the downloaded updates in your system. And deleting it manually would require you to traverse to your /var/cache/apt/archives to remove cached files.

---

