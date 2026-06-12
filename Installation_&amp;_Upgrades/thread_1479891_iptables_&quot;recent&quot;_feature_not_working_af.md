---
title: "iptables &quot;recent&quot; feature not working after upgrade to 10.04"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by joadoor on 2010-05-11
hi there,

i've got a problem with iptables after upgrading ubuntu from 9.10 to 10.04.

the "-m recent" rules are not longer working.
iptables don't accept the lines from my previous ubuntu-version.

here a example:
iptables -A ssh -m recent --set --name counting3
iptables -A ssh -m recent --update --seconds 600    --hitcount 32 --rttl --name counting3 -j DROP

have they anything changed again?? by updating from 9.04 to 9.10 there were some changes too... why do they change the iptables-syntax and defaults from version to version??


i've loaded some more modules (like "ipt_limit ...) and so on. but nothing worked.
hope anyone can help, i've no more ideas  :-(

-joadoor-

---

