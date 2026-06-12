---
title: "resolv.conf file missing in /etc folder"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Neminath on 2008-07-07
i m running nmap on my ubuntu box it requires resolv.conf file to be properly configured.

but in my box the said file is missing. I tried creating one on my own but did not allow to do so even after i used sudo.
is there any way to get rid of this problem.

---

### Post by iaculallad on 2008-07-07
> **Neminath said:**
> i m running nmap on my ubuntu box it requires resolv.conf file to be properly configured.

but in my box the said file is missing. I tried creating one on my own but did not allow to do so even after i used sudo.
is there any way to get rid of this problem.

I'm not sure if creating a blank resolv.conf file could do the trick because this file contains your nameserver (DNS). But, just try.

```
sudo touch /etc/resolv.conf
```

then try to re-run your nmap application.

EDIT: Or try to add your router's IP address to to file.

i.e:

> nameserver your_router_IP_Address

---

### Post by zvacet on 2008-07-07
**system>admin>network>DNS tab**> put your router and nameservers there and close.That should generate resolv.conf file.

---

