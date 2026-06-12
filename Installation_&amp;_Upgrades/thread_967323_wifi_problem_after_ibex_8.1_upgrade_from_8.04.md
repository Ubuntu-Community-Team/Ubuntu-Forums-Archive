---
title: "wifi problem after ibex 8.1 upgrade from 8.04"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by al-76 on 2008-11-01
The wifi on my LG LT-20 which uses ipw2200 stopped after I upgraded to IBEX.

dmesg reports 

 sudo dmesg |grep ipw2200
[   20.476039] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   20.476044] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   20.695941] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.046659] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   21.046666] ipw2200: Unable to load firmware: -2
[   21.046669] ipw2200: failed to register network device
[   21.046745] ipw2200: probe of 0000:02:02.0 failed with error -5

---

### Post by al-76 on 2008-11-01
I have resolved this.  I installed the linux-firmware package, removed and put back the ipw2200 module

sudo aptitude install linux-firmware
sudo rmmod ipw2200
sudo modprobe ipw2200


sudo dmesg |grep ipw2200

[  700.972401] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  700.972414] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  700.977455] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  701.185259] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

---

### Post by gonzo.d on 2008-11-12
Thank you al-76!

Same here with my Samsung Q30 aka Dell Latitude X1, nothing was recognized after the update. Now it works like charm!

cheerio g

---

