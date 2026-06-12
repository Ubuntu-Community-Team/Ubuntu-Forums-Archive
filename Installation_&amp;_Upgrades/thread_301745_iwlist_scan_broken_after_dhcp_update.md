---
title: "iwlist scan broken after dhcp update"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by trubblemaker on 2006-11-17
after the last package upgraded my 

[code ] iwlist scan [/code]

only shows one Cell and that cell is the one I'm associated to.  It won't show any others that are there:
```

meat@troublemaker:~/Desktop$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
meat@troublemaker:~/Desktop$ sudo iwconfig wlan0 essid ubc
meat@troublemaker:~/Desktop$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:34:F2:05:C0
                    ESSID:"ubc"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

anyone know how I can downgrade my packages, and anyone know how I can find the packages?  It was some a*dhcp package, I remeber looking it over thinking it was no big thing but then my scanning broke!  It was working before this as I had a script that used it daily.

FYI I'm on ndiswrapper with bcmwl5.inf.

I can connect to the net, and surf without issue just can't see my near but wireless networks.

---

