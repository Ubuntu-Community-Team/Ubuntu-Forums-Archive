---
title: "removing dhcp"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by rahenri on 2005-05-23
Hi ppl,
at my network, there is a computer which accepts remote booting via DHCP,
but when when I intalled ubuntu, somehow the instalation misunderstood the purpose of that computer and configured my computer to use DHCP and then, neither the network nor the internet was working, i edited the file /etc/network/interfaces a now the internet works but the network still doesn't, is there another file i should edit?
any idea?

[]'s

---

### Post by Xian on 2005-05-23
Just an idea.... look in /etc/network/interfaces.
Should be an entry something like this:

```
# The primary network interface
iface eth0 inet dhcp
```

---

### Post by rahenri on 2005-05-23
the problem is not to configure dhcp, i wnat to remove it, i want to configure using static ip
that is what was this file before
my /etc/network/interfaces is like this now

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        adress 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255

this way internet works, but network doesnt

after that the internet started working

---

### Post by Xian on 2005-05-23
Again, just an idea as I'm not really familiar with this problem but have you looked at possibly using either the  guessnet, switchconf or ifplugd packages. AFAIK, dhcp is provided by the dhcp3-client package.

---

