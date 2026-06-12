---
title: "Ubuntu11.10, Network autoconfiguration failed"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by richard_wu0313 on 2011-10-17
Hi There&#65292;
i used PXE to install ubuntu11.10 amd64, but i met error "Network autoconfiguration failed, your network is probably not using the DHCP protocol". and i checked /var/log/syslog, got possible error message. "dhclient no dhcpoffers received". However, the same way, same machine, same configure, i tried ubuntu 11.04, it's ok. so i doubted maybe some issue in "initrd.gz" and "linux" under folder install/netboot...

Ubuntu guys, could you take a look? thanks!

---

### Post by richard_wu0313 on 2011-10-18
it seemed that ubuntu11.10 would not check ethx one by one, so if your net connection is from eth1, please disable eth0 in BIOS

---

