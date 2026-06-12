---
title: "Manual full disk encryption"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by noorez on 2013-10-13
I manually setup a full disk lvm encryption setup on my laptop. Sometimes however the machine does not boot. It just hangs on the light purple screen. When I do a hard reboot it brings up the prompt for the paraphrase as expected.

I did setup the /etc/crypttab file as expected but are there any other crypt configuration files needed? It seems like certain required files are not getting loaded by the time we get to reading the disks.

---

