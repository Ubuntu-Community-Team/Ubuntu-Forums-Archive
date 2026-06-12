---
title: "feisty install with wep problems"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by stinkyj on 2007-04-26
hi, i'm having some trouble installing with WEP....

it finds my intel 2200BG, no problem, but dmesg is full of this:

eth1: could not initialize WEP: load module ieee80211_crypt_wep
ieee80211_crypt_wep: could not allocate crypto API arc4

is the solution to disable wep for now, or install via eth0?

---

### Post by stinkyj on 2007-04-28
FWIW, i "solved" this by temporarily turning off WEP at the router :\

---

