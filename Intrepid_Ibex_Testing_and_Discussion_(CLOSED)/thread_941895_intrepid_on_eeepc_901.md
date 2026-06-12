---
title: "intrepid on eeepc 901"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xan.scale on 2008-10-08
with hardy much hardware dont works out of box (ethernet, wifi, webcam etc etc)
with intrepid only wifi dont works out of box

using [http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2) wifi works fine. that are free and open source

it's possible that this driver are included in intrepid final?


thz

---

### Post by TheMono on 2008-10-08
Don't think it'll happen. Bug has been filed though. Try this in the meantime: [http://forum.eeeuser.com/viewtopic.php?id=43998](http://forum.eeeuser.com/viewtopic.php?id=43998)

---

### Post by Hershey on 2008-10-08
I have been using the following PPA for the wireless driver on my 1000H:

[http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main

I had to add rt2860sta to /etc/modules to get the driver to load on boot.  Other than that, it has been working great for me.

---

