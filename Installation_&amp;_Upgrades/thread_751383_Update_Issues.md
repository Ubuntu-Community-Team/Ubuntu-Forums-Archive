---
title: "Update Issues"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by gwoodard on 2008-04-10
Okay, I need help, If I install a clean version of Ubuntu 7.10 w/out a internet connection, but connect it afterwards to get updates, but it tells me (and after hitting check) that I am up to date, how can I check that this is so?

---

### Post by ajgreeny on 2008-04-10
You will probably need to enable all the repositories that are not listed in your sources.list file, so go to **System>>Administration>>Software Sources** and enable everything except the source repos and the CD.  Now reload the repos with ```
sudo apt-get update
``` and try again.

---

