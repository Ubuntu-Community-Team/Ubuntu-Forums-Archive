---
title: "I'm stuck: Ubuntu server boots unreliably"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by boudies on 2010-01-16
I am enjoying my very first Ubuntu project, a Karmic 9.1 server on an HP Proliant ML110 G6, but I am stuck: my server boots unreliably - sometimes it does, sometimes it doesn't.

The problem appears to be related to RAID1: if boot fails this is due to a "degraded raid". In my server I want to be safe against a possible drive failure, so I set up /boot, /(root), /var, /usr and /home all on their own RAID1 device. This works fine when the system manages to boot.

I guess my problem must be due to a timing issue during boot, but after a few days now I am not able to find a solution or even a direction in which to search.

Can anyone please offer some help?

---

