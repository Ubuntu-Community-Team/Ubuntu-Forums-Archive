---
title: "still ath9k problems"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mgiacchetti on 2008-09-29
you know guys i'm still having trouble with my ar9280...

Signal is horrible, jumps around constantly, cant surf the web without waiting like dialup..


```

  *-network               
       description: Wireless interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

``````

03:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002a] (rev 01)

``````

ping 192.168.1.1 -c 25

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.109 icmp_seq=1 Destination Host Unreachable
From 192.168.1.109 icmp_seq=2 Destination Host Unreachable
From 192.168.1.109 icmp_seq=3 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=8.21 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.871 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.865 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=0.872 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=0.833 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=0.868 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=0.851 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=0.856 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=2.11 ms

--- 192.168.1.1 ping statistics ---
25 packets transmitted, 9 received, +3 errors, 64% packet loss, time 24029ms
rtt min/avg/max/mdev = 0.833/1.816/8.219/2.297 ms, pipe 3

``````

wlan0     IEEE 802.11bgn  ESSID:"TopTobo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: --its there i just edited it here--
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:-----------   Security mode:open
          Power Management:off
          Link Quality=90/100  Signal level:-37 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

 uname -a
Linux ubuntu 2.6.27-3-generic #1 SMP Wed Sep 10 16:02:00 UTC 2008 i686 GNU/Linux

```

---

### Post by xerosis on 2008-09-29
I'm glad it's not just me, I reported my bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269987](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269987)

I ended up blacklisting ath9k and using ath_pci for the time being, I rely on wireless too much to carry on testing it.

---

### Post by jbernardo on 2008-09-29
I've blacklisted it also, after it locked up tight my Aspire One, at a hotel where it could "see" seven APs with the same SSID.

---

### Post by pytheas22 on 2008-09-29
> I'm glad it's not just me, I reported my bug here: [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/269987](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/269987)

I ended up blacklisting ath9k and using ath_pci for the time being, I rely on wireless too much to carry on testing it. 

I think that the OP's card is only supported by ath9k, not ath_pci, so perhaps you have a different card.  What is the "lspci -nn" line for your card?

> I've blacklisted it also, after it locked up tight my Aspire One, at a hotel where it could "see" seven APs with the same SSID. 

There probably were seven APs with the same SSID--the hotel probably has multiple routers.  It shouldn't have frozen up though.

Did any of you look at the output of "dmesg" when trying to use the ath9k driver?  There might be a clue as to what exactly is wrong.

---

