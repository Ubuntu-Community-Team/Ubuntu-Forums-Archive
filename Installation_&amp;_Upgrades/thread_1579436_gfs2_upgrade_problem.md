---
title: "gfs2 upgrade problem"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by drtomc on 2010-09-21
Hi All,

We just upgraded a small cluster from Hardy Heron to Lucid Lynx and experienced a failure which I'll describe here for the benefit of others.

We're using GFS2 on a Coraid device shared between the three machines of the cluster.

After the upgrade, the mount of the shared filesystem failed, and when we finally located the right location for the relevant log files (/var/log/cluster/*) we discovered that there was a missing device in /dev/misc. The error message (from the log file) was:

cannot find device /dev/misc/dlm-monitor with minor 53

A straight-forward mknod fixed the problem and after restarting the cman service, everything started working again.

cheers,
Tom.

---

