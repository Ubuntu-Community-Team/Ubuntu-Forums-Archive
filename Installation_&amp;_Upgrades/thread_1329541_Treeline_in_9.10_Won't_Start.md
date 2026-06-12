---
title: "Treeline in 9.10 Won't Start"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by booksnmore4you on 2009-11-17
Do you have this problem, too?  Here's the solution.

The version in Synaptic is not the latest Treeline Version 1.2.4, which contains a work-around for a bug in PyQt 4.6's clipboard support that could prevent TreeLine from starting.  1.2.4. also fixes unrequested horizontal scrolling to the left in the tree view when the selection was changed.[[1]("http://freshmeat.net/projects/treeline/releases/306601")]

To fix the issue, uninstall Treeline from synaptic and install the 1.2.4. deb package from [http://packages.debian.org/squeeze/all/treeline/download](http://packages.debian.org/squeeze/all/treeline/download)

Your system will complain that an older and better supported version is available in Synaptic.  Ignore the prompt and install anyway.

---

