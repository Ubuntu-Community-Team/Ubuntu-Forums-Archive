---
title: "NTP or Chrony?"
date: 2023-11-21
forum: Installation &amp; Upgrades
---

### Post by georgy-trubetkoy-ru74 on 2023-11-21
Why timesync-service should I use on the Ubu/Deb servers?
I read some articles, and the result is Chrony only.
I also know about systemd-timesyncd, but it can't work in NTP-server mode.
What do you think about it?

---

### Post by ActionParsnip on 2023-11-21
Choose which you prefer and use that across all systems. I like Chrony but that's just my personal preference

---

### Post by SeijiSensei on 2023-11-21
I just use good old ntpd.

---

### Post by TheFu on 2023-11-22
I was using ntpd, then Canonical decided to swap in systemd-timed as the default. Fine, except it wasn't keeping accurate enough time, so I looked for a replacement and found Chrony. Spent about 10 minutes installing chrony onto all my systems and setting up a chronyd server on my time server. Be happy with sub-sec correct time ever sense.  

Initially, I had to manually disable and mask systemd-timed, but just installing chrony-anything now does that. From a few different clients:
```
$ chronyc sources
210 Number of sources = 1
MS Name/IP address         Stratum Poll Reach LastRx Last sample               
===============================================================================
^* istar                         3   6   377    44  -3104ns[  -26us] +/-   41ms


$ chronyc sources
MS Name/IP address         Stratum Poll Reach LastRx Last sample               
===============================================================================
^* istar                         3   6   377    55  +3386ns[  -22us] +/-   41ms
```

I did look at the newer time standard, ptp, but it seemed more complex for a local-only requirement. I don't need amazing accurate times, just within a few seconds is sufficient. For me, having all the log entries matched is most important.

Every time I find something wrong with a systemd-provided service, I find an alternative solution.  systemd-resolved started this.  If they just worked, I'd have not bothered, right?

---

