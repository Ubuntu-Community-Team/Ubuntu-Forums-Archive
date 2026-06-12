---
title: "Wireless stopped working on upgrade to 10.04"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by azmyth on 2010-05-15
Wireless was working without issue in 9.10. I can no longer connect to my WPA2-AES network after upgrading. I don't use network manager due to dropped connections so I just setup my connection through /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.0.4
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
wpa-driver wext
wpa-ssid mynetwork
wpa-ap-scan 1
wpa-psk xxxxxxxxx

auto eth0
iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
```

I'm using a USB Zydas device

```
Bus 002 Device 005: ID 0ace:1215 ZyDAS WLA-54L 802.11bg
```

iwconfig wlan0 gives

```
wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

sudo iwlist scan wlan0 works only as superuser

```
Cell 01 - Address: 00:11:50:C9:A9:3D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level=48/100
                    Encryption key:on
                    ESSID:"mynetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f5d1615369
                    Extra: Last beacon: 860ms ago
                    IE: Unknown: 000B576946694E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020013

```

Any suggestions?

---

### Post by azmyth on 2010-05-16
I can connect if I turn encryption off.

---

### Post by azmyth on 2010-05-22
Upgrade to 10.04 didn't install wpa_supplicant for unknown reasons then having eth0 and wlan0 with the same static ip caused an issue.

---

### Post by Gyanos422 on 2010-05-22
I have a similar problem. I'm using Ubuntu 10.04 on my laptop and for some reason it will only connect to my router when i set the security as WEP which i don't want to do. I want to use WPA2 (worked in windows but the manufacturer makes drivers just for windows, so i figured it was a problem like that)

I didn't check to see if it worked on a previous version because i went right to 10.04 on it.

---

### Post by azmyth on 2010-05-23
Which device are you using and how are you trying to connect? Are you using network manager or through the /etc/network/interfaces file?

---

