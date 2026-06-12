---
title: "How to dowmload once but upgrade 3 systems?"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by j.s.rood on 2007-01-25
I installed ubuntu 6.10 from a LFX-DVD and did an upgrade with synaptec, so I have now 240 *deb packages in /var/cache/apt/archive.

I would like to reuse these 223 MB *deb's on two computers with identical ubuntu systems installed on a site with only a 56Kb modem.

Would that be possible? Would a simple « for d in *.deb ; do ; apt-get $d; do »? 
Should I instead put the lot on a usb-stick and somehow add the stick to the repository-list?

any hint would be most welcome.

js.rood

---

### Post by dcstar on 2007-01-26
> **j.s.rood said:**
> I installed ubuntu 6.10 from a LFX-DVD and did an upgrade with synaptec, so I have now 240 *deb packages in /var/cache/apt/archive.

I would like to reuse these 223 MB *deb's on two computers with identical ubuntu systems installed on a site with only a 56Kb modem.

Would that be possible? Would a simple « for d in *.deb ; do ; apt-get $d; do »? 
Should I instead put the lot on a usb-stick and somehow add the stick to the repository-list?

any hint would be most welcome.

js.rood

I believe you could copy the deb cache files from the updated PC to all the others, and I think that there is a HOWTO on having a local update repository (do a search for it).

---

