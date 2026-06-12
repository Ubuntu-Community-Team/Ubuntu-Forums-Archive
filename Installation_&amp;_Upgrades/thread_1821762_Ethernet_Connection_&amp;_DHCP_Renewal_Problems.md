---
title: "Ethernet Connection &amp; DHCP Renewal Problems"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by Xanko on 2011-08-09
I just upgraded my Ubuntu Server from 10.04 to 11.04. I am having issues with the ethernet connection upon boot. The connection will blink slowly and not stay connected to the network. If I then unplug the ethernet from the switch and then replug it in, eth0 will get a steady connection, at which point I have to run the following command to get everything working.

```
sudo dhclient eth0
```

After running the command I have no issues with the ethernet connection.

**lshw -C network **

```
*-network:0             
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: eth1
       version: 0d
       serial: 00:0e:0c:4d:21:9f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:fc241000-fc241fff ioport:7400(size=64) memory:fc200000-fc21ffff
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: eth0
       version: 02
       serial: 00:0e:0c:4d:1f:3a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=10.1.1.100 latency=52 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:23 memory:fc220000-fc23ffff ioport:7440(size=64)
```

**dmesg | grep "eth0"**

```
[    1.658510] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   62.153856] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  217.088375] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  217.088735] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  227.292013] eth0: no IPv6 routers present

```

**/etc/network/interfaces**

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```

Not sure if anything else is needed, please assist me in troubleshooting this issue and determining if it is an actual bug.

---

### Post by Xanko on 2011-08-12
Any Ideas?

---

