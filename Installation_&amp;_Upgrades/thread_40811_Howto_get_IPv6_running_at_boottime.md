---
title: "Howto get IPv6 running at boottime"
date: 2005-06-10
forum: Installation &amp; Upgrades
---

### Post by dsmarty on 2005-06-10
I use both IPv4 and IPv6 and I use static IP adresses for both of them.
I found some debian documentation and I edited /etc/network/interfaces.
It looks like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 10.0.0.4
        netmask 255.0.0.0
        gateway 10.0.0.254
iface eth0 inet6 static
        address 2001:888:1b24:1::4
        netmask 64
        gateway 2001:888:1b24:1::ffff

```

This works perfect when I boot with the default interfaces file (dhcp on eth0), bring down eth0 with "ifdown eth0", add the text above to the interfaces file and bring up the interface again with "ifup eth0"

But, when I reboot the system, somehow it doesn't work, the interface is brought up, the IPv4 address is configured, but the IPv6 address is not. Even worse, the ifup and ifdown script fail to recognise eth0 when booting with this config. (while the interface is (at least for ipv4) up and running)

What am I doing wrong ?
I searched through google, the man-pages etc, but I couldn't find anything.

---

