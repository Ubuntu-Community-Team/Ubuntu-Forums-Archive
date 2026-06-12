---
title: "Help with wireless connection on ACER 3212 laptop"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by firdooze on 2006-03-09
I've been trying to get my wireless to work on my ACER 3212 since last 2 weeks but to no avail... anyone can kindly help me?

the problem is I cant seem to connect to my wireless network... I'm using centrino... 

I did some searchin but cant seem to get what i want... here's what I got...

```

iwconfig>> 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"firdooze"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:88:22:61:D1
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:3532-3031-3132-3132-3334-0000-00   Security mode:open
          Power Management:off
          Link Quality=92/100  Signal level=-36 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:5

sit0      no wireless extensions.


```

```

iwlist eth1 scan >>

eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:7A:4A:47
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=46/100  Signal level=-73 dBm
                    Extra: Last beacon: 122ms ago
          Cell 02 - Address: 00:12:88:22:61:D1
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 18 22 6 9 12 24 36 48 54
                    Quality=91/100  Signal level=-37 dBm
                    Extra: Last beacon: 55ms ago


```

```

ifconfig>>

eth1      Link encap:Ethernet  HWaddr 00:12:F0:9B:2D:F6
          inet6 addr: fe80::212:f0ff:fe9b:2df6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:48630 (47.4 KiB)  TX bytes:10092 (9.8 KiB)
          Interrupt:10 Base address:0x6000 Memory:b0001000-b0001fff



```

any help will be good! thanks! :mrgreen:

---

### Post by firdooze on 2006-03-10
anyone?? please?

---

