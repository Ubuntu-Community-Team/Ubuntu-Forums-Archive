---
title: "Using ath9k in Intrepid"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2008-09-15
I am a little bit confused. My wireless card should work out of the box with ath9k. This module has been included in 2.6.27, however I cannot get my wireless card to use it. Network Manager says it is using ath5k. If I add ath9k to my modules file and blacklist ath5k wireless doesn't work. 

Is there a way of using ath9k instead.

Thanks
George

---

### Post by hanzomon4 on 2008-09-15
Did you upgrade or install any drivers yourself?

---

### Post by inportb on 2008-09-15
ath9k is in the kernel, so i guess one could install the drivers oneself by rebuilding a kernel without ath9k, but that does not make much sense in the context of ubuntu ;p

---

### Post by hanzomon4 on 2008-09-15
Shouldn't have to the latest alpha provided working wireless for my macbook pro out of box via ath9k. Sure your card is an ath9k supported card? 802.11n compatible card right?

---

### Post by gmclachl on 2008-09-16
Yeah it is supported and the module is loaded. However the card refuses to use the ath9k driver and loads the ath5k instead. 

George

---

