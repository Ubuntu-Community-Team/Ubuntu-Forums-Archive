---
title: "Wireless problems with new kernel 2.6.35"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by no_name.pdf on 2010-10-31
Hello there! I've just downloaded the last release 10.10 and I discovered that it doesn't work correctly with my wireless card. The wi-fi router is 6/7m far and signal is good:
```
iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"my-wireless-connection"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
```2.6.32-25 works correctly and it connects successfully. By 2.6.35 it tries to connect, but it isn't able to do it: to made the laptop connected i have to come with it near the router and then, i can come back to the original position an surf the net. Can you solve this problem?

Here it is my wireless card:
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

---

### Post by no_name.pdf on 2010-11-02
no one can help me?

---

