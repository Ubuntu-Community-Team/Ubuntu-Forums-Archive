---
title: "Fake Nvidia GTX970 (GM204) on kubuntu"
date: 2019-06-14
forum: Installation &amp; Upgrades
---

### Post by klode82 on 2019-06-14
My wife make me a present, a graphic card GTX970, but it is a Chinese Fake.
It is really a GT550Ti, with 1GB VDDR5, 192bit, 192 Cuda Core. Here the link: [https://www.banggood.com/GTX970-1GB-GDDR5-192Bit-900MHz-3600MHz-Gaming-Video-Graphics-Card-p-1263730.html?cur_warehouse=CN](https://www.banggood.com/GTX970-1GB-GDDR5-192Bit-900MHz-3600MHz-Gaming-Video-Graphics-Card-p-1263730.html?cur_warehouse=CN)

So, I want to install anyway on my PC, I haven't had a Nvidia Card.
My PC is a Pentium E2180 with 4GB DDR2 with kUbuntu 18.04

When I install Nvidia driver, kUbuntu give me always a window: Driver Manager, and it give me a list of driver (from 390 to 430), but even I use one of this, it continues to show me this window. I don't think the video card is installed correctly.
Who can help me to understand much more?

---

### Post by deadflowr on 2019-06-14
Are you saying every time you login you see the Driver Manager window?

It might be you have restore previous session settings set in System Settings.
Look in Settings >> Startup and Shutdown >> Desktop Session (in the On Login section).
It might be set for restore previous session.
Switch that to open empty session, or whatever it's now called.

---

### Post by rbmorse on 2019-06-14
It may be Nouveau is all you can use with this card, given its origins.  

I don't know if the Nvidia driver does any validation checking of/with/against the card's vBIOS, but given Nvidia's other practices I would not be at all surprised.

---

### Post by oldfred on 2019-06-14
If it really is a GT550, you can only install the 390 driver.

 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Fermi based should use 390.xx not newer
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus](https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus)

---

