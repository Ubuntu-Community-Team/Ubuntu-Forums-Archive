---
title: "ntp &quot;pool&quot; capability broken in package in 16.04"
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by dgeist on 2016-05-13
I just upgraded to 16.04 on my workstation. The ntpd package included (4.2.8p4+dfsg-3ubuntu5) appears to have done away with the capability to automatically import a list of servers from a DNS round-robin as a pool. Now I get this when I use the directive "pool stratum2.services.mydomain.com":

```
root@host:/home/dgeist# ntpq -pn
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 stratum2.servic .POOL.          16 p    -   64    0    0.000    0.000   0.000
root@host:/home/dgeist#
```

If I state "server stratum2.services.mydomain.com" multiple times, I get seemingly corrrect behavior (or more accurately, behavior like the pre-pool versions of ntpd):

```
root@host:/home/dgeist# ntpq -pn
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 2XX1:578:2:1109 172.30.1.33      2 u   12   64    1   59.881    0.286   0.000
*2XX1:578:15:110 172.17.1.243     2 u   12   64    1    7.780    0.283   0.000
 2XX1:578:2:1109 172.30.1.33      2 u   12   64    1   59.952    0.287   0.000
root@host:/home/dgeist#
```

Is there some reason this version of Ubuntu has done away with the support? My updated EL7 devices appear to be running on a patched version of 4.2.6.

Dan

---

### Post by dgeist on 2016-05-13
I may have answered my own question. Adding the following to ntp.conf seems to allow the proper behavior:
restrict source nomodify noquery notrap

Anyone know why the new behavior?

Dan

---

