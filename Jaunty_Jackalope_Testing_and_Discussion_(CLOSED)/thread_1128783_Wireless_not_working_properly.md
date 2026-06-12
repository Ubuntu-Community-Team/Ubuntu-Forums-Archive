---
title: "Wireless not working properly"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rcoelho on 2009-04-18
Hi,

I've upgraded sometime ago to Jaunty and recently I noticed a trouble on connecting with my wireless. It seems like a bad password. It's on WPA2, Sometimes it takes like 20 minutes till I get connected. And also sometimes it's intermittent, it simply disconnect and ain't conect anymore.

Anyone knows something?

---

### Post by Peter09 on 2009-04-18
What are the specs for your machine? I Have a Toshiba M40 and wireless is a real pain on that. Its intermittent and sometimes requires a complete power off to get it to work.

post the output of
 ```
ifconfig
```

and
```
lshw -C network
```

to show your specs

---

### Post by Jenkins1 on 2009-04-18
I has this problem and changed the encryption to WEP. I can connect anywhere now.

---

### Post by MacUntu on 2009-04-18
Do NOT use WEP. WEP offers no protection. Better use Ubuntu 8.10 with WPA than 9.04 with WEP.

---

### Post by lisati on 2009-04-18
Probably good to use a combination of techniques. I use  a combination of WPA or WPA2 and MAC Access filters.

---

### Post by Jenkins1 on 2009-04-18
[QUOTE=Macuntu]Ubuntu 8.10 with WPA than 9.04 with WEP.[/QUOTE]

I had the same problem in Ubtuntu 8.10 
now changed to WPA only and not WPA and WPA2 personal. It appears to work.

---

### Post by rcoelho on 2009-04-18
Hello my ifconfig output :

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:62:25:39
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fe62:2539/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:81386654 (81.3 MB)  TX bytes:15745428 (15.7 MB)

and lshw -c produces: 

*-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:62:25:39
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.12 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn

Any other ideas why WPA2 wouldn't work? In 8.10 was just fine.

---

