---
title: "Firefox very very slow to load/open websites"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-05-13
I have freshed installed lucid.
Linux ubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
The problem is firefox is very very slow to open web sites.

---

### Post by jflaker on 2010-05-13
I've seen this...

Unless you are running IPV6, you should turn it off because FF will try IPV6 before IPV4

In the FireFox location bar type
```
about:config
```

Confirm you want to be there then

in the search bar type

```
ipv6
```

Set network.dns.disableIPv6 to TRUE....

---

