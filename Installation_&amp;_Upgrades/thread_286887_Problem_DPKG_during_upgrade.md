---
title: "Problem: DPKG during upgrade"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by DJ Wings on 2006-10-28
I tried upgrading my Xubuntu system to 6.10 from 6.06.1, and now it refuses to start X. This isn't the main problem; I could normally just use "sudo apt-get dist-upgrade", which would fix the problem. But dpkg is coughing up errors now, too...
> 
dpkg: parse error, in file /var/lib/dpkg/available, near package "cpio", line 2: value for "status" field not a llowed in this context.
Any suggestions? I tried using dpkg --configure -a --force-all, and still nothing.
By the way, I screwed around in the file a bit, tryng to fix it myself, but I have a backup. I also used the Update Manager to do the upgrading, instead of hacking /etc/apt/sources.list (which I tried before, without success).

---

