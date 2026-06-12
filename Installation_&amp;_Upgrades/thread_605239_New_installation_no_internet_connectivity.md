---
title: "New installation no internet connectivity"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by jetj on 2007-11-06
I installed Gutsy from CD and had no internet connection. I altered the IPV6 and can connect with Firefox Browser now however my Evolution mail and the Repositories do not connect at all to the internet.

I'm unable to update or get my mail. My knowledge is very basic.
Thanks
Jet

---

### Post by zvacet on 2007-11-07
Network manager>manual configuration>network>select yout modem>properties>select type of connection>close>DNS tab>replace DNS you see with yours>close>back to network>chek your modem and box with **chenging network interfaces** will show.After that close.Applications>accessories>terminal>type

```
pppoeconf
```

---

