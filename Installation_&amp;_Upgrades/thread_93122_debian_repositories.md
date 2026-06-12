---
title: "debian repositories"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by mc_bizon on 2005-11-21
what would happen if i was using debian repositories on ubuntu?

---

### Post by Pablo_Escobar on 2005-11-21
1. Dependency problems - I mean serious dependency problems.

It's not a crime to test a Debian **package** on Your system, but to setup a **Debian repos** and then apt-upgrading or even apt-getting would lead to serious damage.

---

### Post by mc_bizon on 2005-11-21
so normal user (not tester) shouldnt use debian repositories

thank you

---

### Post by az on 2005-11-21
That is correct.  You shouldn't.  The problem is not so much the dependancies, but that some things will properly install according to the available versions and dependancies, but since the packages are built for two differing environments (Ubuntu has ubuntu-specific tweaks) you may silently break stuff.

---

