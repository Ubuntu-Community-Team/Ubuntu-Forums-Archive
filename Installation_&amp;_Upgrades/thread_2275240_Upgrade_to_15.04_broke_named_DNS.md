---
title: "Upgrade to 15.04 broke named DNS"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by gstanden on 2015-04-25
I run named DNS and upgrade to 15.04 broke it.  Any advice?  I am goiing to go through reinstalling it tomorrow according to my instructions at [https://sites.google.com/site/nandydandyoracle/oracle-12c-rac-asm-flex-cluster-on-ubuntu-14-10#TOC-Setup-DNS-and-DHCP-for-System](https://sites.google.com/site/nandydandyoracle/oracle-12c-rac-asm-flex-cluster-on-ubuntu-14-10#TOC-Setup-DNS-and-DHCP-for-System)

---

### Post by TheFu on 2015-04-25
I'd review the changelog for the specific version of BIND you are running.
IMHO, running an non-LTS release for a server is a mistake.

---

