---
title: "ipv6 in Lucid"
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-12-15
There is no ipv6 with vanilla kernel line (2.5.32-8 and 2.6.32-999) here on my system. Previously I had to use ipv6.disable=1. Is ipv6 turned off by default or did I kill it in some other file that I can not remeber now ...? No, I do not need it, quite opposite ...

---

### Post by zika on 2009-12-16
> **zika said:**
> There is no ipv6 with vanilla kernel line (2.5.32-8 and 2.6.32-999) here on my system. Previously I had to use ipv6.disable=1. Is ipv6 turned off by default or did I kill it in some other file that I can not remeber now ...? No, I do not need it, quite opposite ...Mistake is mine. Once upon a time I've edited /etc/sysctl.conf and added net.ipv6.conf.all.disable_ipv6=1 so that is the reason ipv6 was disabled.

---

