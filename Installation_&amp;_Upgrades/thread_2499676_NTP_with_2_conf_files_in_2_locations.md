---
title: "NTP with 2 conf files in 2 locations"
date: 2024-08-06
forum: Installation &amp; Upgrades
---

### Post by matthys on 2024-08-06
I just moved from 22.04.4 LTS to 24.04 LTS and notice some strange configuration for NTP:

It seems there are 2 and I wonder why and howto:
[B]/etc/ntp.conf
/etc/ntpsec/ntp.conf[/B]

It seems both look the same, but are they both used?

Thanks,
Matthijs

---

### Post by currentshaft on 2024-08-06
.

---

### Post by matthys on 2024-08-07
Okay,  I wanted to remove ntpsec as I didn't install that one myself. And it also removed ntp. It seems if you install ntp it also installs ntpsec.
But because I removed and purged ntpsec (and ntp), both config were gone. After installing ntp (and ntpsec) I only have one: [B]/etc/ntpsec/ntp.conf

[/B]I guess this has something to do with upgrade where old stuff is not removed, which confused me.

I also checked your suggestion and:# ps -ef | grep ntpd
ntpsec      1426       1  0 14:36 ?        00:00:00 /usr/sbin/ntpd -p /run/ntpd.pid -c /etc/ntpsec/ntp.conf -g -N -u ntpsec:ntpsec

Thanks!

---

