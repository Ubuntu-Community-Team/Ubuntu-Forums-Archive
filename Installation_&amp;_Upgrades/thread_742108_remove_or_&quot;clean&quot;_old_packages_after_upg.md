---
title: "remove or &quot;clean&quot; old packages after upgrade"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by thebrotherofasis on 2008-04-01
Hello,

I recently upgraded to hardy 8.04 beta from gusty 7.10. The issue is that when completed the upgrade, by mistake, I chose "keep", instead of "clean" or "remove" old packages.

Actually, what I really wanted is to clean or remove the old packages. I hope there is a way to do that after having chosen a different option. II want to free up space, and not have obsolete packages on my system

Any commands on how to do this?

Thank you very much

---

### Post by forestpixie on 2008-04-01
You can use apt-get to clean the downloaded packages, 

```
sudo apt-get clean
```
from the man page - 
clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. 

```
sudo apt-get autoclean
```

Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless.

---

### Post by kellemes on 2008-04-01
How to remove not used packages, meaning packages not needed by any other.
Check the output before hitting "y"
```
sudo apt-get autoremove
```

---

