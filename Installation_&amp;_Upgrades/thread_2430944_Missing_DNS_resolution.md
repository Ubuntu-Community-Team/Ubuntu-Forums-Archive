---
title: "Missing DNS resolution"
date: 2019-11-09
forum: Installation &amp; Upgrades
---

### Post by BigBadWoofer on 2019-11-09
Since upgrading to 19.10 I don't always get DNS service to start. I can fix the problem with the following:

     sudo systemctl restart systemd-resolved.service

It does work occasionally so it may be a timing problem. Perhaps something happened in the upgrade from 19.04. Where should this happen in the startup sequence?

---

### Post by ubfan1 on 2019-11-09
Do you get any errors from searching syslog?  sudo grep resolv /var/log/syslog  If you get a line like systemd-resolved[1053]: Using degraded feature set (UDP) for DNS server 192.168.1.1,try adding the package libnss-resolve to tweak the /etc/nsswitch.conf file.  Maybe the service is running, but just not working.

---

