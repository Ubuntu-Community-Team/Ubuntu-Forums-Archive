---
title: "instal dhcp"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by Blackfangz on 2012-04-15
Package dhcp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source. what does this mean for my network??:mad:

---

### Post by haqking on 2012-04-15
> **Blackfangz said:**
> Package dhcp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source. what does this mean for my network??:mad:

```
sudo apt-get install dhcp3-server
```

I presume you want a DHCP server ?

---

### Post by darkod on 2012-04-15
Another option for a very simple dhcp server is dnsmasq:
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

---

