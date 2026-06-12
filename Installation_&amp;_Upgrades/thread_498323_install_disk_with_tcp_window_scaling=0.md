---
title: "install disk with tcp_window_scaling=0"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by Jon Irons on 2007-07-11
Does anyone know of a way of making a Feisty Desktop install disk with tcp_window_scaling=0

I've had the following experiences:

Standard feisty desktop install cd will stops at about 82% and then completes. Initial installation is not able to browse most websites etc. Setting content of /proc/sys/net/ipv4/tcp_window_scaling=0 fixes browsing, apt etc.

Alternate feisty install (I actually want to use lvm) stops at 40% and after some 36 hours has still not completed. Its waiting for apt to scan repositories.

The standard desktop cd has tcp_window_scaling=1 and doesn't seem to be editable once booted.

It seems to me that I need a desktop (actually alternate) cd  with tcp_window_scaling=0 at boot time, but I'm not sure how to set about doing this. Two options occur to me:
1 - find a suitable configured iso image
2 - edit some parameter on the existing iso image using some suitable procedure (not sure what this would involve).

Anyone have any hints for me?

---

