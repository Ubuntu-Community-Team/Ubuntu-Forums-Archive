---
title: "System not responding to Software Sources command"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by sgcharest on 2008-10-31
In addition to the problems in my previous post, I attempted to re-download 8.10 thru the web site using Software Sources in "Administration."  Software sources does not respond.  

Any thoughts?

---

### Post by maybeway36 on 2008-10-31
Try typing in this terminal commands:
```
ping -c 4 archive.ubuntu.com
```
If it doesn't work, but the Internet still does, then the Ubuntu servers are probably overloaded.
If it does work, it's probably some sort of configuration problem.

---

