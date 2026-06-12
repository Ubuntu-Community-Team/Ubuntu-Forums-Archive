---
title: "non-executable /tmp"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by dninja on 2005-09-10
Is there anyway to get apt-get to check whether /tmp is mounted with the exec flag set before trying to run install scripts which need to execute things unpacked to /tmp.

I have /tmp on its own partition and it is mounted without execute permissions, occasionally when installing a package it all bombs out because it tries to execute something and fails.

A check from apt-get would be nice, maybe a paused warning that to give you time to bail out, remount then start again?

---

