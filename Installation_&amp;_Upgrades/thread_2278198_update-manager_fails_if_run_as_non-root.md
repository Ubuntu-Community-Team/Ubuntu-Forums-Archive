---
title: "update-manager fails if run as non-root"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by ishwest on 2015-05-14
Hi!

If I run update-manager from my account it just crashes silently. But when I run it as root it works ok.

Problem is this effectively disables automatic updates which is a nuisance :-(

I'm running Ubuntu 15.04 but had the same problem in 14.04 before I upgraded a few days ago.

Any suggestions how to fix this? Or where to look for some log records of the crashes?

Thank you!

---

### Post by bapoumba on 2015-05-14
What is the output to :
```
update-manager
```

You can update/upgrade with :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ishwest on 2015-05-15
Thanks for the answer but my problem solved itself. Right after I posted to this forum the update-manager started working as intended :-)

Closing the thread since I can't reproduce the problem anymore.

---

