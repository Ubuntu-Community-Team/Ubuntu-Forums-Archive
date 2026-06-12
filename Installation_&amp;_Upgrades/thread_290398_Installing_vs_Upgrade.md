---
title: "Installing vs Upgrade"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by davedean on 2006-11-01
Hi,

So after wondering about it for a while, I decided that I'd install Edgy on a separate partition, as well as having a Dapper that I'd upgraded to Edgy already. I figured that I could use one of them to track Feisty (I'm used to breakage, and don't mind tracking unstable releases :) ).

So I've gone ahead an done that - I now have a "Dapper->Edgy" which takes 40+ seconds to boot, and a "Fresh Edgy" which takes 20 seconds to boot, and in general the "Fresh Edgy" feels significantly faster.

So I'm wondering .. is there any known reason that a "Dapper to Edgy" install is so much noticeably slower? 

Beryl also seems much more stable on my "Fresh Edgy" install. 

Any devs that would be interested in me running some testing for them between the two installs?

---

### Post by Jussi Kukkonen on 2006-11-01
Before comparing you should probably check that you have the same startup scripts running (/etc/rc2.d/) and that you have similar desktop sessions (maybe you could create a new user on both systems).

---

