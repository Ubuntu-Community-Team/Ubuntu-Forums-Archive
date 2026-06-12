---
title: "use of d-i pkgsel/install ????"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by bazzer on 2006-09-25
Hi
I'm preseeding an install using the well documented method [here]("http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apcs01.html") and I've got to the part where I need to install a basic set of packages.
I don't understand the options I can pass to the line:
d-i pkgsel/install-pattern string ~t^ubuntu-standard$

Can I just put a package there? Or do I apt-get (or aptitude) it?
I'll need to install quite a few packages so I just need to know how to pick them up in the preseed file, not select a predefined 'role' for the PC such as Desktop, Print Server etc...
TIA

---

