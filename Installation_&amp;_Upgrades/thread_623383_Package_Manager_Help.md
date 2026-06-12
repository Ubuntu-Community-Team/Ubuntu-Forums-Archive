---
title: "Package Manager Help"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by delsydebothom on 2007-11-25
Okay, I was installing a package and it stopped installing. I couldn't get the package manager to exit, so I restarted the computer (in the correct manner). When it came back up, I got into Synaptic Package Manager, thinking I was going to have to repair some broken packages. This came up:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I got into the terminal, and entered that in, and it responded:

dpkg: requested operation requires superuser privilege

So what now?

---

### Post by El Lance-O on 2007-11-25
You want to type 'sudo' before 'dpkg --configure -a'.

You have to use sudo to do pretty much anything to your system. Get used to using it.

---

