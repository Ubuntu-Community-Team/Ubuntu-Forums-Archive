---
title: "Could not get lock"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by KaYnemO on 2008-04-21
Out of nowhere, my apt-get says this when trying to update:

: sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Can' t seem to find the cure! Any advice?

---

### Post by Partyboi2 on 2008-04-21
Make sure you don't have add/remove or synaptic package manager open at the same time as you enter the update command in the terminal.

---

