---
title: "failed to open configuration file '/home/user/.dpkg.cfg'"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by support on 2008-08-12
(Running Ubuntu 8.04LTS)

The last time I ran <sudo apt-get update> and <sudo apt-get upgrade> everything worked fine. Today, when I run <sudo apt-get upgrade> most of the packages being upgraded return the following error when being setup:

failed to open configuration file `/home/username/.dpkg.cfg' for reading: Permission denied

Any ideas on what I am now missing?

---

### Post by mike-g2 on 2008-08-19
Nope, but getting the same error on multiple machines.

Mike

---

### Post by guldi on 2008-09-03
Afaik, the problem ist nfs.
When your /home directory ist mountet via nfs, the local root (wich is called by local sudo) does not have any rights.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=200701](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=200701)

Even it's not very nice, if there's no solution, I could live with it.

---

