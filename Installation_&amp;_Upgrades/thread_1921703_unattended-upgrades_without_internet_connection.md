---
title: "unattended-upgrades without internet connection"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by surfer on 2012-02-07
hello

i'm trying to get [FONT="Courier New"]unattended-upgrades[/FONT] to run. the problem is: the machines i want to upgrade with it are not connected to the internet; i have a local mirror.

unfortunately [FONT="Courier New"]/etc/cron.daily/apt[/FONT] - the script that reads the unattended-upgrades config files and runs the upgrade - does not terminate.

my guess is: as the script calls [FONT="Courier New"]apt-key net-update[/FONT] which seems to rely on an internet connection, it just hangs there.

is there a way to remedy this?

(this is on ubuntu 10.04.2 LTS )

---

### Post by surfer on 2012-02-21
bump.

---

