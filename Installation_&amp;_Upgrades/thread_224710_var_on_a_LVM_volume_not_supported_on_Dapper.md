---
title: "/var on a LVM volume not supported on Dapper"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by accumulator on 2006-07-28
It seems mounting an LVM volume on /var isnt possible with the Dapper release. 

First, the loopback interface (lo) didnt get 127.0.0.1 assigned to it, because /var/run didn't exist after a fresh Kubuntu install (it is created after /etc/rcS.d/S35mountall.sh is started, so it ended up on the LVM /var)

I fixed that by going into single-user mode and creating /var/run manually on the root filesystem.

But now eth0 doesn't get started, because when ifup -a is started from /etc/rcS.d/S40networking the /var/run/network/ifstate file contains a 'started' state for eth0. So basically, when shutting down the PC, the network interfaces are brought down _after_ /var gets unmounted (modifying state on the 'normal' /var), and started again after a reboot _after_ /var gets mounted (modifying state on the LVM /var).

---

