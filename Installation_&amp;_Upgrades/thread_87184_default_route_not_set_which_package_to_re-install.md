---
title: "default route not set which package to re-install?"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by metoo on 2005-11-07
Hi,

on a machine which I try to upgrade from debian sid to breezy (yeah, don't! It's not mine and I wanted to spare the personal re-configuration...) the default route is not set during boot.

/etc/network/interfaces has an entry: gateway xxx...
and I can bring up the route (to a router) with:
route add default gw xxx.xxx....

Hence, it is not done automatically at boot. Does anybody know, where the difference is breezy vs debian sid? It worked before. Which package would bring the logic to do this (scripts etc...)?

---

