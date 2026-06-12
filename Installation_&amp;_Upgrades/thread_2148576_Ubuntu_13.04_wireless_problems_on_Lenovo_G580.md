---
title: "Ubuntu 13.04 wireless problems on Lenovo G580"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by Heinzelmannchen on 2013-05-25
I can't get my wireless card (BCM 4313) to connect to the internet. I tried multiple guides but to no avail, i tried installing B43 and had a connection for a few seconds although it was so weak i couldn't even use it. I'm sorry to be asking this i'm sure it gets irritating seeing all the noobie questions when there are guides but i've followed a few and can't get it working. In the system settings it says BRCM propiety driver is not working. Luckily i have an ethernet connection so i'm hoping this will be an easy fix. All help is appreciated.

lspci | grep Network
```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off 
```

---

### Post by Heinzelmannchen on 2013-05-26
The following commands worked
```
sudo apt-get update
``` 
```
sudo apt-get -y install broadcom-sta-common
``` 
```
sudo reboot
```

But the connection is only 3 bars when it should be stronger any ideas on how to make the connection stronger? I have full bars on ubuntu 12.1

---

