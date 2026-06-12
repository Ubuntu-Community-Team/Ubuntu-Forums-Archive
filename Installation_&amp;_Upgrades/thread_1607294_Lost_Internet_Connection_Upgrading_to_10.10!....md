---
title: "Lost Internet Connection Upgrading to 10.10!..."
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by VcDeveloper on 2010-10-27
Just upgrade my main server vrom 10.04 TLS to 10.10 using the update manager.  Everything ran smoothly but lost internet connection after the successful install.

...but my kvm vm's can connect so I'm assuming it maybe my interface setup:

```
auto lo
iface lo inet loopback

auto br0

iface br0 inet dhcp
    bridge_ports    eth0
    bridge_stp      off
    bridge_maxwait  0
    bridge_fd       0

```

should this effect my internet connection?

---

