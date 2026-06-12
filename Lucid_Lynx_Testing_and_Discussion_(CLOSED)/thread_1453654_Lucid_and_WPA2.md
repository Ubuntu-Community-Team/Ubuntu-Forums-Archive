---
title: "Lucid and WPA2"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by robbie_tzr on 2010-04-13
Hi all,

I've got a Netgear WG602 with DD-WRT firmware installed. I tried changing the wireless security to WPA2 just out of curiosity, but my netbook running Lucid UNR refuses to connect. I note that the wireless connection dialogue box says WAP and WPA2 personal, so I assumed the latter was supported. Is this an "issue"? Not really too fussed as I just changed it back to plain old WPA and it works fine, but still a little curious!

Rob.

---

### Post by chili555 on 2010-04-13
> Is this an "issue"?Not that I have heard of. I have been trying the live CD and have no trouble at all, either with Network Manager or with manual configuration, connecting to my WPA2-PSK network. Do your card and driver support WPA2?```
sudo iwlist wlan0 auth
```Substitute your wireless interface, if it's not wlan0.

---

