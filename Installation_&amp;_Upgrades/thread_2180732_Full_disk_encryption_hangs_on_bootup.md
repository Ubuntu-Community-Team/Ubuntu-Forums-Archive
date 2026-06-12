---
title: "Full disk encryption hangs on bootup"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by noorez on 2013-10-14
I manually setup a full disk lvm encryption setup on my laptop. Sometimes however the machine does not boot. When I turn my machine on, it just hangs on that blank light purple screen. When I do a hard reboot (because nothing responds), this time it brings up the prompt for the paraphrase as expected.

I did setup the /etc/crypttab file as expected but are there any other crypt configuration files needed? It seems like certain required files are not getting loaded by the time we get to reading the disks so it doesn't know how to read the encrypted volume.

---

