---
title: "upgrading to edgy query"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by mewt on 2006-09-26
hi, 

me and my sister both use ubuntu 6.06 on our respective systems and we intend on doing dist-upgrades whenedgy is out..however it is quite a hard hit on our download limit..so what id like to ask is:

will one of us be able to do a dist-upgrade and then the second rig updates from the first one ?

---

### Post by daller on 2006-09-26
After upgrading the first machine, simple copy the content of /var/cache/apt/archives/ to the other machine.

Then run an "apt-get update" on the other machine, and an "apt-get upgrade" - The upgrade then checks if anything is already downloaded! (And it is, since /var/cache/apt/archives/ is the directory for downloaded apt-files!)

Enjoy!

---

