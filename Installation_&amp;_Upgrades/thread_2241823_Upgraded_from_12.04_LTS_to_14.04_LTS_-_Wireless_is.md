---
title: "Upgraded from 12.04 LTS to 14.04 LTS - Wireless issue"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by gary-hawes on 2014-08-28
Hi.

Been trying to fix this for a few days and its not happening but:

As the title says i've upgraded to 14.04 and now my wireless sometimes doesnt resume the connect it had when I closed my laptop. I've even done the old restart to try and see if that would 'reset' anything but no luck. The issue mainly happens when I close my laptop lid.

Any help much appreciated.

---

### Post by gary-hawes on 2014-08-28
my ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 20:1a:06:8b:81:7f            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:206564 (206.5 KB)  TX bytes:206564 (206.5 KB)


wlan0     Link encap:Ethernet  HWaddr 0c:d2:92:ad:2c:30  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ed2:92ff:fead:2c30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32004 (32.0 KB)  TX bytes:35762 (35.7 KB)



```

iwconfig

```

wlan0     IEEE 802.11bgn  ESSID:"Searching...."            Mode:Managed  Frequency:2.437 GHz  Access Point: 20:0C:C8:7C:B3:B8   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.

```

---

