---
title: "Best way to control the start of services"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by elektronaut on 2007-08-23
Hi,

there are several ways to prevent the start of services during boot, for instance BUM, update-rc.d and changing the 'S' and 'K' characters in /etc/rc?.d/[SK1-9]*servicename to lowercase. I prefer the command line, so I'd rather not use BUM. As I read that update-rc.d might get you into trouble by changing the priority number that it assigns to a previously suppressed service, I thought that the 'lowercase method' might be the best. What do you think? And in case you agree, should I only change the start entries ([S1-9]*servicename) to lowercase or also the kill entries ([K1-9]*servicename)? What happens if I start e.g. a database manually but forget to kill it before shutdown and the kill entry is also deactivated? Is this relevant at all?

---

