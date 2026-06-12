---
title: "Can Ubuntu Software &amp; Update panel/Other Software content be clean ?"
date: 2023-04-16
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2023-04-16
I am using ubuntu 23.04.
after some updates and upgrades I am let with many unused entries in 
Software & Update panel/Other Software panel
is there away to remove the unused entries in command line ?
Tks

---

### Post by TheFu on 2023-04-16
23.04 hasn't been released yet. There's a different sub-forum for pre-released distros.

Typically, the repositories are stored in files under /etc/apt/.  You can use **sudoedit** to modify those text files. Don't screw up the files and make backups BEFORE touching them.

---

