---
title: "Problems With Wireless Internet"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by bigguy_132 on 2006-10-27
Alrighty guys I am fairly new to linux and am having a big problem. I got my wireless internet to work on Drapper. I have a Dell Wireless 1390 Broadcom card. I used ndiswrapper V1.17 and used the drivers. This worked perfectly. I did an upgrade to edgy last night. The problem I am having a problem with my wireless. In Drapper it was wlan0 and I had no problem connecting. When I upgraded my wireless changed to eth1. I cant configure the wireless properties at all. It cant find any access points or anything. I uninstalled ndiswrapper completely and did reinstall. I cannot get my wireless to work, my wireless light to come on as it did in drapper. I did do a ifconfig and I do see it there. Any help would be appreciated! If I cannot get this to work I will most likely just do a reinstall. Thanks in advance. :)

---

### Post by jd65pl on 2006-10-27
Does it show if you do...
```
iwconfig
```

can you find it on this list of cards which worked previously but now dont?
[http://ubuntuforums.org/showthread.php?t=281660](http://ubuntuforums.org/showthread.php?t=281660)

---

### Post by bigguy_132 on 2006-10-27
Yes it does show. It shows under eth1. I just followed another tutorial and I uninstalled ndiswrapper 1.17 and upgraded it to 1.23. I follwoed the instructions and managed to get my wireless to work. It switched my wirelss from eth1 to wlan0. But when I rebooted it went back to eth1 and wouldnt work. So I have no idea what to do.

---

### Post by bigguy_132 on 2006-10-29
any ideas anyone?

---

