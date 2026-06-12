---
title: "[Solved] Synaptic search problem 8.10 Intrepid"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by combatwombat_nz on 2008-11-03
FYI:

I had problems with Synaptic on a fresh install. It could not find anything with the quick search feature, it couldn't find somethings (eg Thunderbird, wine) with the normal search, and yet the CLI sudo apt-get install worked happily.

I found the solution to be: In Synaptic Repositories, set the Download From the Main Server, rather than my local server. Then Close, Reload, then set back to local server.

Hope that helps someone else :-D

---

### Post by windfix on 2008-11-05
Thanks, totally helped me.  I could scroll through the entire repository list of software, but neither quick or normal searches brought up anything outside of the official ubuntu (with logo) packages.

Awesome.

---

### Post by monkeyking on 2008-11-06
isnt this related to this one [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)

---

