---
title: "Destination Net Unreachable with repeater"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by joecripps on 2013-11-01
Hope you can help!

Just installed Ubuntu server.  All good.  But, I cannot connect to the internet.  Not good.

My setup is as follows:

- Connected PC to wireless repeater via ethernet port
- Router address 192.168.1.1
- Repeater 192.168.10.1

I can ping the repeater but not the router..cannot get to the net..why won't the connection just work as it does with my Windows laptop?

I have tried a static IP but to no avail.

---

### Post by tgalati4 on 2013-11-01
You have a Class C network, so check your network mask.  It should be 255.255.0.0.

Examine, but don't post:

```
netstat -r
```

---

