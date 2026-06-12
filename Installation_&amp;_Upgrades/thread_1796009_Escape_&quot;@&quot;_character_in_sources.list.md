---
title: "Escape &quot;@&quot; character in sources.list"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by Linfreak on 2011-07-03
Hi all, [https://bugs.edge.launchpad.net/ubuntu/+source/gnome-terminal/+bug/130289](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-terminal/+bug/130289), while this bug talks about proxy settings, I am having problems when using https repo links in sources.list which have a username or password with the @ character. Is it possible to escape the @ character in sources.list?

eg: deb [https://user:xyz@123@host:port](https://user:xyz@123@host:port) dists folder

APT takes 123@host as the host instead of just host and xyz as password instead of xyz@123.

Cheers,
Siva

---

