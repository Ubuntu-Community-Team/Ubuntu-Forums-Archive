---
title: "?SLI and Raid0?"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by FhaeTon on 2005-09-24
Does anyone know if ubuntu works with raid0? I got my setup going but it obnly sees to harddrives and not them combined.

---

### Post by mlomker on 2005-09-24
[QUOTE=FhaeTon]Does anyone know if ubuntu works with raid0? I got my setup going but it obnly sees to harddrives and not them combined.[/QUOTE]

Hardware or software?  The 'raid' built into system boards actually require a driver to work and many of them don't have linux drivers available (you'll have to check your Mobo manufacturer's website).

There is a software RAID that uses LVM, called mdadm-raid, but I've never set it up.  I'd imagine a search would turn a few things up.

---

