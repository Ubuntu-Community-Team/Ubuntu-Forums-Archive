---
title: "Won't Connect To WiFi"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by viper3ez on 2010-01-04
just upgraded my dell m ini 10 from the factory 8.04 to 9.10. from what i see everything works but it wont connect to my WiFi.
 
is there anyway to scan for available wireless signals and just connect? or do i have to type in the SSID evverytime i want to connect to wireless. is there any known issue with this?
 
help please

---

### Post by pcal on 2010-01-04
Hi viper,

I recently put 9.10 netbook remix on my Fujitsu M2010, and had the same trouble initially. In my case, what had happened was that the wifi/bluetooth radio had defaulted to off state in hardware, so 9.10 didn't see it, and consequently didn't install anything for it.

As soon as the radio was back on, it was detected and set up automatically.

So all I can suggest from experience is to make sure the wifi radio is on...

Hope it helps,

Pcal

---

### Post by viper3ez on 2010-01-05
thanks pcal, i wiped the system and installed the 32bit 9.10 cos i really did not like the netbook remix layout. its already hard enough using the dell mini 10. i was able to install the broadcom wifi driver which was the culprit and is a very popular problem. i did package install and it worked. thanks

---

