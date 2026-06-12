---
title: "wifi not as good with 9.10 alpa 5"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by geovino on 2009-09-04
I gave 9.10 Alpha 5 a try as live CD and I see where It wants to install a wifi driver. Why? with 9.04 wifi is detected automatically. This is a step backward. Please keep 9.10 wifi detection as good as 9.04.

I hope this is becasuse its Alpha 5 and the final version corrects this problem.

---

### Post by Michael.Godawski on 2009-09-04
Moved to Karmic. :P

---

### Post by Cuba71 on 2009-09-04
My results are totally opposite, I installed Karmic A-5 in a very old laptop, Gateway Solo, and I'm using a $10 wireless card, Belkin F5D070A, and it's recognized automatically and get an excellent signal. I guess YMMV

---

### Post by jbernardo on 2009-09-04
I had to take out NetworkManager (and knetworkmanager) because it would do background scans that would hang the ath9k driver for more than a minute if I was using a 802.11n network. on a 802.11b or 802.11g I had no such problems. I installed Wicd and now 802.11n works, as wicd doesn't resort to background scans - but until kernel 2.6.31-8 the background scans didn't have this effect.

---

### Post by zenarcher on 2009-09-04
I had to resort to wicd with Alpha 4 in order to connect my wireless.  Now, with Alpha 5, I don't need wicd anymore, as knetworkmanager is working fine.  I'd say that's a step forward.

Cheers,
zenarcher

---

