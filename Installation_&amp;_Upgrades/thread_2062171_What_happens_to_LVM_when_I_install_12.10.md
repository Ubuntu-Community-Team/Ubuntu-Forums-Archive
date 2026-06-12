---
title: "What happens to LVM when I install 12.10?"
date: 2012-09-24
forum: Installation &amp; Upgrades
---

### Post by yay101 on 2012-09-24
Hey all! I have a relatively strange configuration, I use a media server/ htpc that currently runs 12.04 and xmbc to service the tv and a few pc's on a home network.

I am not sure if I will upgrade to 12.10 yet as it will depend on if there are any benefits for my specific system.

The main current issue with a possible upgrade is whether LVM will be able to just pick up where I shutdown before the upgrade.

Important notes:
The boot drive is not in the LVM.
There are 5 drives sdb through sdf.

Anyone have any ideas how this would go or what steps I would need to take to ensure a working system after boot?

---

### Post by darkod on 2012-09-24
The LVM should be fine during the upgrade (never have tried it myself), but why would you upgrade a server to 12.10?

The 12.04 is supported 5 years and the 12.10 will be only 18 months.

Besides, you don't usually upgrade servers just because a new release is out, usually they are upgraded LTS to LTS.

---

