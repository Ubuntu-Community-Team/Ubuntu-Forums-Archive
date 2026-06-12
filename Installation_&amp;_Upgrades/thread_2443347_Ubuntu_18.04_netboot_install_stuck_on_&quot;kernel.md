---
title: "Ubuntu 18.04 netboot install stuck on &quot;kernel: random: crng init done&quot;"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by jakuro on 2020-05-14
Today I find out that Ubuntu netboot preseed installer downdloaded from:
kernel [http://cz.archive.ubuntu.com/ubuntu/dists/bionic/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/linux](http://cz.archive.ubuntu.com/ubuntu/dists/bionic/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/linux)
initrd [http://cz.archive.ubuntu.com/ubuntu/dists/bionic/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/initrd.gz](http://cz.archive.ubuntu.com/ubuntu/dists/bionic/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/initrd.gz)

is stuck on kernel: random: crng init done.
As well i don't see any disk in /sys/block even HDD are there.

Any idea?

EDIT: Looks that same behavior is for Ubuntu 16.04

Fixed.. Doesn't matter OS when there is firewall on the way. Would be nice some timeout tho.

---

