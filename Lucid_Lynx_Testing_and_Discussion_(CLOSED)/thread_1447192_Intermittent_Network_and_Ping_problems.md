---
title: "Intermittent Network and Ping problems"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bhagwad on 2010-04-05
I'm on a dual boot with Ubuntu Lucid (10.04) and Vista.

Every now and then my wired network stumbles and during browsing, I get "looking up..." which never resolves.

It's not a DNS problem because when this happens, I can't even ping my router. ping 192.168.1.2 (router IP) gives me nothing, no message and no diagnostics. The cursor just moves to the next line and stays there.

I can't ping any website like google using either ping google.com or ping 209.85.231.104. The ping just doesn't work.

Currently the only way to get my network working again is to create another network manually with the same settings and then switch between them. This seems to clear up the problem till the next time it happens.

Another way for me to kickstart the network is to visit my wireless router admin page on the browser (even though ping doesn't work, I can still connect on Firefox). Just viewing the page instantly brings the network back to life.

This doesn't happen in Vista though and I've also disabled ipv6 from grub. Any ideas as to why this is happening?

---

