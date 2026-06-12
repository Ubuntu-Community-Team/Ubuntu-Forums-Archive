---
title: "Correct way to get internet connection at boot"
date: 2009-07-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ketchers on 2009-07-08
Since lately karmic has had problems getting X up and running after an update, it would be nice to have wireless so one could do an upgrade from the terminal. So here is the question: How do you get a wireless network (WPA2) up from the terminal - or better yet at boot (say from your list of automatic ap's - that the nm seems to know about) and at the same time have nm behave as usual, i.e., scan for available networks, etc.?

---

### Post by b3n87 on 2009-07-08
Hey, there is a command to use your wireless at the terminal when X isnt running.

I dont have time to get the exact command but i know its on the Arch Wiki:

[http://wiki.archlinux.org/index.php/Wireless_Setup#Part_II:_Wireless_Management]("http://wiki.archlinux.org/index.php/Wireless_Setup#Part_II:_Wireless_Management")

---

### Post by Reiger on 2009-07-08
Alternatively you just install WICD as your network manager which starts before X. Thus, once configured, WICD will automatically connect to a network before X starts.

---

### Post by MacUntu on 2009-07-08
Google for wpa_supplicant(.conf).

In my case I simply run ```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -B
sudo dhclient
```

with the /etc/wpa_supplicant.conf containing info for my WPA2 network:
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

and I'm connected.

---

### Post by mrsurb on 2009-07-08
I love that... 'simply'... but thanks a lot!

---

