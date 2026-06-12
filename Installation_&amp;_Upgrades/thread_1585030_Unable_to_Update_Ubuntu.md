---
title: "Unable to Update Ubuntu"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Garnenia on 2010-09-29
When running Update Manager I am given an error message and it won't complete the update. I tried uninstalling the program clementine but it didn't help and now I have no idea where to go from here.  Any ideas?

> Failed to fetch [http://ppa.launchpad.net/me-davidansome/clementine/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/me-davidansome/clementine/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drs305 on 2010-09-29
> **Garnenia said:**
> When running Update Manager I am given an error message and it won't complete the update. I tried uninstalling the program clementine but it didn't help and now I have no idea where to go from here.  Any ideas?

Open synaptic or software sources, go to Settings, Repositories, Third Party/Other Software tab and untick the me-davidans... repository. Then press the RELOAD button on the menu.

That repository is unavailable - the server is down, the packages aren't available, etc - probably temporarily. You can try again later if you know that repository has worked in the past.

---

