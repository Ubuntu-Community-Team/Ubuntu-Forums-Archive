---
title: "[ubuntu] DNS not working after upgrade to 17.10 can I downgrade to 16.04lts or 17.04?"
date: 2017-11-06
forum: Installation &amp; Upgrades
---

### Post by mschet on 2017-11-06
I'm having a heck of a time trying to get DNS working in Ubuntu 17.10, never had a problem before.. ([https://ubuntuforums.org/showthread.php?t=2376649](https://ubuntuforums.org/showthread.php?t=2376649))  I've tried every bit of advice I could google, the last one being "install unbound"...umm...I get dns errors when installing unbound, so that's a dead end...

I'm just about ready to give up, and would just like to install 16.04 instead - can I do this without losing my files and settings, etc?   I'm dual booting to windows where I have internet.

---

### Post by spiritinvader on 2017-11-15
I have a similar problem. I recently did a release upgrade from LUbuntu 16.04 to LUbuntu 17.10 and I'm unable to access the internet. This issue applies to both ethernet and wifi.

Trying out some suggestions from Googling, I figured that the issue is that the DNS nameserver is unavailable/inaccessible to the network manager(?). It appears that `systemd-resolve` sets nameserver to 127.0.0.1#53 and when I add OpenDNS nameservers to `/etc/resolvconf/base` it doesn't have any effect. 

Opening lines of my networkmanager.conf file are
```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

```

I discovered that after the latest upgrade, I no longer have dnsmasq installed. 

**How should I configure the network to read the DNS nameserver correctly?**

---

