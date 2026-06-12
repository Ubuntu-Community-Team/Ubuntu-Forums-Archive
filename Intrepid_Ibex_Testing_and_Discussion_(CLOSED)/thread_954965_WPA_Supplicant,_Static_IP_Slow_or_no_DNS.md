---
title: "WPA Supplicant, Static IP Slow or no DNS"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Das Oracle on 2008-10-21
I want to be rid of NetworkManager and KNetworkManager so I went about trying to setup my static IP with WPA-2 and all that jazz. I got it to where I can connect to the router, ping IP addresses but I can't ping any [www.example.com](www.example.com) dns names. I was able to fix it by adding my router IP (10.0.0.1) or my router's dns addresses to /etc/resolv.conf

```
nameserver 10.0.0.1
or
nameserver xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
```

however when I do that my browsing of websites is terribly slow for the lookup and on sites that I may want to view more than one page it tends to never load after 2 or 3 clicks.

here is my cat /etc/network/interfaces file

```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 10.0.0.2
gateway 10.0.0.1
broadcast 10.255.255.255
dns-nameservers 10.0.0.1 ***Or*** xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx ******
netmask 255.0.0.0
wpa-driver wext
wpa-ssid MyDlink
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <wpa-key>

```

if I don't have anything setup in resolv.conf I can't do DNS resolutions and can't use a browser, but when I do use resolv.conf DNS resolution works but seems incredibly slow and buggy. Any ideas?

---

