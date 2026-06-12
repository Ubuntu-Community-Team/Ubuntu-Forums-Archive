---
title: "Can't add new network connection"
date: 2016-03-09
forum: MINT
---

### Post by michael358 on 2016-03-09
I am trying to connect to a VPN using Mint Xfce. In Network connections I am able to select "add new connection", "PPTP", but I am unable to edit anything in the next box because it is greyed out.  Also Network Settings is completely greyed out. There is no Network Connections tab visible at the lower right of the screen either. I am currently connected to the internet with Wifi.

---

### Post by jeremy31 on 2016-03-10
Try ```
sudo apt-get install network-manager-openvpn-gnome
```

May need a reboot

---

### Post by michael358 on 2016-03-11
Thanks jeremy. That worked.

---

