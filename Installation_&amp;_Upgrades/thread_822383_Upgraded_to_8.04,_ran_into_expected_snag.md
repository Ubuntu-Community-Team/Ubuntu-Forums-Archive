---
title: "Upgraded to 8.04, ran into expected snag"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by djmoore85 on 2008-06-08
Hey yall, I finally took the plunge and downloaded and installed 8.04. Ran into an expected snag with my Broadcom 4318 wireless card, the device is recognized, the ndiswrapper program and windows driver say they are working, but for some reason I cannot get the power turned on to it. I currently have to connect through ethernet. Any suggestions or help? Here are some code outputs, hope they are helpful
```
lspci

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

 ```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:06:f0:17  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe06:f017/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1654537 (1.5 MB)  TX bytes:152865 (149.2 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146400 (142.9 KB)  TX bytes:146400 (142.9 KB)

```
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"klinger"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Pumalite on 2008-06-08
Open up all your repos and run:
sudo apt-get update
sudo apt-get upgrade.

---

### Post by djmoore85 on 2008-06-09
Hey thanks man that worked like a charm, what exactly did I do there by running those commands?

---

### Post by Pumalite on 2008-06-09
You used the unleashed power of Ubuntu.

---

### Post by rzrgenesys187 on 2008-06-09
> **Pumalite said:**
> You used the unleashed power of Ubuntu.

:)

sudo apt-get update downloads the latest package list from the repositories
sudo apt-get upgrade downloads updates to any packages you have installed that have newer versions in the repositories

be careful when running sudo commands that you are unsure of in the future

---

### Post by Pumalite on 2008-06-09
If you want to get specific; I think you needed the backports.

---

