---
title: "Unknown unit : user@1000.service"
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by zkab on 2015-02-14
I had the same error in syslog both for Ubuntu server 14.10 and 15.04
I upgraded from 14.10 -> 15.04 with:

sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade -d

but I get this error:

systemd-logind[2970]: Failed to start user service: Unknown unit: [email]user@1000.servic[/email]e

How can that be fixed ?

---

### Post by bapoumba on 2015-02-14
Maybe there ?
[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756247](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756247)

---

