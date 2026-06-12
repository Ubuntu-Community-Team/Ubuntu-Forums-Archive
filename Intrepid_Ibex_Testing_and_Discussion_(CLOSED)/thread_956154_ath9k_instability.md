---
title: "ath9k instability"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Goofee691 on 2008-10-22
with the latest group of updates from 10.22.2008 the ath9k driver does not stay connected for more than 15min and at times only lasts a single min.

i noticed that networkmanager now also shows the proper network speed instead of 1mbps

---

### Post by maestrobwh1 on 2008-10-23
Same deal here with ath5k.  I had to manually install madwifi from source for now.

I like the concept, but it just isn't working correctly yet.

---

### Post by Goofee691 on 2008-10-23
does the madwifi driver work as a replacement for the ath9k driver? its the only reason why i started running intrepid pre alpha6 since for hardy you had to install the ath9k driver and then i had problems with network manager

---

### Post by Marshal0505 on 2008-10-23
> **Goofee691 said:**
> does the madwifi driver work as a replacement for the ath9k driver? its the only reason why i started running intrepid pre alpha6 since for hardy you had to install the ath9k driver and then i had problems with network manager

I temporarily used the madwifi driver as a replacement for ath9k due to instability with the latter.(it kept freezing my computer on wpa connect).
But now all problems are solved i'm really enjoying the stability of ath9k.

---

### Post by Goofee691 on 2008-10-24
ok well instability still exists with the latest update to the 2.6.27-7 kernel but i have no problems with the wireless if i boot the 2.6.27-6 kernel other then it reporting a connection speed of just 1mbps

---

### Post by sloggerkhan on 2008-10-24
I've had very poor overall results, sometimes getting radio calibration errors, with the ath5k/ath9k kernel driver.

---

