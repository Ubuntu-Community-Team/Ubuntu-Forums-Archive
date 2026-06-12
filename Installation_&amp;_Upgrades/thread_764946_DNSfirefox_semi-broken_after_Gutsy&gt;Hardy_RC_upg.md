---
title: "DNS/firefox semi-broken after Gutsy&gt;Hardy RC upgrade"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by topynate on 2008-04-24
I upgraded to Hardy last night and rebooted. Firefox will no longer resolve addresses - it immediately goes to a page failed to load screen. Some other programs seem able to resolve addresses, e.g. ping, and giving firefox an IP address works OK. Synaptic has a problem too. I'm using an rt2500 type wifi card on a 64bit system.

---

### Post by topynate on 2008-04-24
I've fixed the problem in firefox now, by setting network.dns.disableIPv6 to true in about:config. I'm now trying to disable IPv6 for the whole system to clear up the other problems.

---

### Post by dcm2007 on 2008-04-25
I too am having this issue with firefox after upgrading the Hardy! Many other apps can access the internet just fine, but not firefox.  It was working great under Gutsy.  Why would anyone make IPv6 the default? It's not widely used yet!

---

