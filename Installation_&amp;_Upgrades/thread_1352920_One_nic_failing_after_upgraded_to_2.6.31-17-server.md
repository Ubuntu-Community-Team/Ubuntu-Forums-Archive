---
title: "One nic failing after upgraded to 2.6.31-17-server"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by niklasn on 2009-12-12
Having upgraded yesterday (2009-12-11) using do-release-upgrade to 2.6.31-17-server I am stuck with one out of two nics. The internal 192-nic works fine, but the public cannot be reached publically. curiously enough /usr/bin/ssh was set to '000' during the upgrade.

ufw is disabled, iptables is disabled.

Calling the webserver on 192... works fine as does ssh on the internal address. No public access seems possible.

---

