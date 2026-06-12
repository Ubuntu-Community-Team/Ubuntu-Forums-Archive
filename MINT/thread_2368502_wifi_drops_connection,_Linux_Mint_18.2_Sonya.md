---
title: "wifi drops connection, Linux Mint 18.2 Sonya"
date: 2017-08-11
forum: MINT
---

### Post by avi30 on 2017-08-11
wifi keeps dropping every 5 mins. 

Pastebin link - [https://pastebin.com/YuK6g9u2](https://pastebin.com/YuK6g9u2)

---

### Post by wildmanne39 on 2017-08-11
*Thread moved to **MINT for a better fit**.*

---

### Post by jeremy31 on 2017-08-11
Try disabling UFW and you may have to set a BSSID in Network Manager for the connection as there are quite a few AP's with the same name
Disable wifi powersave with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

