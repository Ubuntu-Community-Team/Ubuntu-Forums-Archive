---
title: "Internet not connecting after upgrade to 9.10"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by krishnamohan on 2009-11-22
I upgraded to 9.10 yesterday...GUI was not working so had to install the video driver...


Now I find that it does not detect the connected networks...maybe again a driver problem..


How do I find if network driver is installed? I

---

### Post by poohman on 2009-11-22
Please give more information regarding the problem,
What type of network card are we talking about? I mean, is it a wireless card ur talking abt? maybe a lspci would help

---

### Post by krishnamohan on 2009-11-23
Hmmm..its a Realtek one ....lspci gives me 

***mii      5212      8139too,8139cp***


Network manager says that the device for network connections is not managed....

---

### Post by krishnamohan on 2009-11-24
I changed

*** [ifupdown] managed=false ***

to **true** in

*** /etc/NetworkManager/nm-system-settings.conf.***


Now it works!!!!

:D

---

