---
title: "partner-images.canonical.com no IPv6"
date: 2023-02-17
forum: Installation &amp; Upgrades
---

### Post by msankalpa on 2023-02-17
partner-images.canonical.com has no IPv6 address and its not reachable from IPv6 only networks.

```
#nslookup partner-images.canonical.com dns.google
Server:  dns.google
Address:  2001:4860:4860::8888

Non-authoritative answer:
Name:    partner-images.canonical.com
Address:  185.125.188.67
```

---

### Post by ActionParsnip on 2023-02-17
You can work around by adding public resolvers to your /etc/resolv.conf file (it seems)
[https://serverfault.com/questions/596616/how-do-i-reach-ipv4-addresses-from-an-ipv6-only-network](https://serverfault.com/questions/596616/how-do-i-reach-ipv4-addresses-from-an-ipv6-only-network)

---

