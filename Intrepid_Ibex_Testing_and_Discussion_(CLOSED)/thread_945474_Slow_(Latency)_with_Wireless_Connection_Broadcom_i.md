---
title: "Slow (Latency) with Wireless Connection Broadcom in Intrepid"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ps2wayne on 2008-10-12
Hello,
So I am running intrepid 8.10 on my hp laptop (dv8000). It has a wireless broadcom card (06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)). 

Now I was able to get it "working" and connected to my router with the hardware driver enabled (B43 wireless driver), though connection speeds are horrible. Very slow and/or intermittent. Pages will take forever to load. If I ping an ip I will see packet loss. Now if I connect directly to the router through ethernet all speeds are back to normal and I see no connection problems.

$ uname  -r
2.6.27-7-generic

wlan0     IEEE 802.11bg  ESSID:"604"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:FA:3D:B1   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/100  Signal level:0 dBm  Noise level=-11 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any ideas how to resolve this?

---

