---
title: "deja dup back up tool"
date: 2019-02-03
forum: Installation &amp; Upgrades
---

### Post by mikealte2468 on 2019-02-03
I am in the process of building Ubuntu 18.04 system and want to perform back ups as I progress.

Unfortunately, when I start this utility I get a message to install duplicity and python-gl. Click install and get error msg that E: dpkg was interrupted and needs to to be manually installed.

This package comes with the install image.

Can some one suggest what to do?

Thanks

---

### Post by TheFu on 2019-02-04
First, ensure the system is fully patched, with no package management errors.

**sudo apt update && sudo apt upgrade**
If it says to reboot, do that.   If there are any errors, those need to be fixed.

Next, **sudo apt install duplicity python-gl**  - I'm assuming your spelling and the specific packages are correct. Duplicity makes perfect sense, as deja dup is based on it.  I don't use any of those tools for my backups, so I don't actually know, but duplicity does check all the right boxes for what a good backup solution provides.

---

### Post by mikealte2468 on 2019-02-05
Thanks! Problem solved.

---

