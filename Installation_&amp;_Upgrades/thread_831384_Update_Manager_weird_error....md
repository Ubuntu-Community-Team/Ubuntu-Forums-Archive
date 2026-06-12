---
title: "Update Manager weird error..."
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by Sneaky07 on 2008-06-16
Hi I'm running 8.04 and when I try and update in the update manager I get this error:

```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

I'm sort of new to Ubuntu but I've never seen this problem before any help would be great!  Thanks!!

---

### Post by avtolle on 2008-06-16
Generally, the error you posted comes when there is another package manager open. So, were you in Synaptic, e.g., and had it open when you tried to update?

---

### Post by Sneaky07 on 2008-06-16
I guess I must have but I didn't realize it.  I've never seen that error before though but it is working now thanks!!

---

### Post by avtolle on 2008-06-16
No problem. I've wondered about the following behavior I've noticed, and whether this is a part of the problem you (and others) were having. Following an update/upgrade/installation of new software from Synaptic, Add/Remove, or the terminal, the "cog wheel" or the arrow (for security updates) turns gray/appears in the panel gray for a period after exiting Synaptic, et al., which signifies "A Package Manager is working". This leads me to believe that after one believes he is done and has exited Synaptic, e.g., some "behind the scenes" stuff is going on, and until the wheel/arrow is gone from the panel, the error you encountered will happen, even though the user is certain he/she is not using another package manager. Just an observation coupled with some thoughts.

---

### Post by Junkieman on 2008-06-17
I had a similiar issue, and am posting the solution i used for anyone interested.

Just note that my locked cache problem had a completely different reason behind it (vmware), but if your */var/cache/apt* cache has been locked, try this to release the lock:

```
sudo apt-get -f install
```

The system tray notification icon turns from gray to red, signalling that the systm can now pereform updates.

---

