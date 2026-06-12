---
title: "Ubuntu Pro activation on 3rd ubuntu server Ubuntu 22.04.1 LTS"
date: 2022-10-08
forum: Installation &amp; Upgrades
---

### Post by valeriancafe on 2022-10-08
Help... ***_ Ubuntu Pro activation on 3rd ubuntu server Ubuntu 22.04.1 LTS_***

System information as of Sat Oct  8 05:54:36 PM EDT 2022

  System load:  0.16357421875       Processes:              184
  Usage of /:   24.6% of 109.47GB   Users logged in:        0
  Memory usage: 14%                 IPv4 address for bond0: 192.168.1.4
  Swap usage:   0%

 * Super-optimized for small spaces - read how we shrank the memory
   footprint of MicroK8s to make it the smallest full K8s around.

   [https://ubuntu.com/blog/microk8s-memory-optimisation](https://ubuntu.com/blog/microk8s-memory-optimisation)

0 updates can be applied immediately.

$ sudo ua status

SERVICE          ENTITLED  STATUS    DESCRIPTION
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
livepatch        yes       disabled  Canonical Livepatch service

ERROR: Unable to configure Livepatch: Failed running command '/snap/bin/canonical-livepatch config remote-server=https://livepatch.canonical.com' [exit(1)]. Message: error executing config: livepatchd error: daemon shutting down

Enable services with: pro enable <service>
ok the problem is after installing on server it disable livepatch and I can't turn it on again :( . When I first installed Ubuntu server I activated Canonical Livepatch service it on install 

how do I turn it on again :confused:

Thanks

---

