---
title: "KDE - No Wireless Networking"
date: 2009-05-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fifth on 2009-05-18
For the past few days I've been unable to connect wirelessly from KDE.I've tried to connect using the Plasmoid and also with KNetworkManager. Neither connects.

The Plasmoid will continually prompt for a password every couple of minutes but never connect.

With KNetworkManager just does not connect.

Wired networking on KDE works fine. I can log into Gnome and use wireless without any problems.

I tried creating a new user account to check if it was a config issue, but the new user cannot connect either.

Is there anything else I can try?

---

### Post by MacUntu on 2009-05-18
Same here. Maybe this is a kdepim/kdewallet problem? For me it connects fine without NM by just using wpa_supplicant with a proper wpa_supplicant.conf config file:

```
sudo /etc/init.d/NetworkManager stop
sudo killall wpa_supplicant
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf &
sudo dhclient

```

With /etc/wpa_supplicant.conf containing:
```
ap_scan=1
network={
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        ssid="MYSSID"
        psk="MYKEY"
}
```

for my network (WPA2 + DHCP).

---

### Post by fifth on 2009-05-18
For now I've removed the network plasmoid and connect with the Gnome network manager, it connects without problems. But would be good to get back to the native KDE versions.

---

### Post by fifth on 2009-05-18
Thanks MacUntu.

Can you specify more than one network in wpa_supplicant.conf? I need roaming between home and office.

---

### Post by MacUntu on 2009-05-18
AFAIK it should be sufficient to just add another "network={...}"-section. I'm only using this way as a workaround for NM problems so I'm not too familiar with wpa_supplicant configuration.

---

### Post by caryb on 2009-05-18
Mine has not stopped working with WEP connection through the 4.2 -> 4.3 upgrade.


Cary

---

