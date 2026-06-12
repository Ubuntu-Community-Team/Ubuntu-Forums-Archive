---
title: "Ubuntu 9.10 internet"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by chrisj26 on 2010-02-26
I've downloaded and tried several versions of Ubuntu 9.10, and I've never managed to get my internet working. Has anyone ever encountered the same issues? I can connect to my wireless network fine but I can never browse with firefox. At one point I managed to ping google but not since. I've tried them on more than just one computer. I've tried switching to WICD and changing the browser but no difference.

---

### Post by Steven_B on 2010-02-26
Sorry, we need a bit more information to point you in the right direction. The output from the commands below would be helpful.

What network card(s) are you using?
```
sudo lshw -class network
```

Can you get an IP address? 
```
ifconfig
```

How is your network set up?  Do you have a router, or some other connection?

---

### Post by spectralblue on 2010-02-27
Yes that's quite strange. You can connect but you have no internet? 

Ah, I just remembered. This happened to me in windows as well, I can connect but I'm unable to go to any webpage. For some weird reason, my stupid router is not giving the proper DNS to my machine for some reason.

Try manually setting the DNS perhaps?

---

### Post by chrisj26 on 2010-03-05
```
*-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1b:fc:e3:71:b2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A latency=0 link=no module=atl1 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wmaster0
       version: 01
       serial: 00:13:46:93:8f:d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=10.1.1.4 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:93:76:62:2d:9f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```
I'm doing this from Jaunty as I don't have 9.10 running on any machine but I will try it from a LiveCD.

---

### Post by cjhabs on 2010-03-05
I had a similar situation and the problem was that the machine, before the rebuild, had a static IP address - after the rebuild it had a dynamic address - the router did not like that.
My solution was to change to use the same static IP - as I wanted to use it as a network file server anyway. Everything burst into life after that.

---

### Post by chrisj26 on 2010-03-15
I was able to ping google and several other websites so I think it may be browser settings which seems strange. I tried and tried (various websites) eventually firefox pulled up google but wasn't able to get any other page up.

---

### Post by chrisj26 on 2010-03-17
I've managed to get FF browsing. It turns out the problem was with IPv6 being enabled! I'm now trying to get those setting applied system-wide cause right now synaptic does not work/update! if anyone has any clue as I'm trying all tutorials I can find oneline with no luck!

---

### Post by chrisj26 on 2010-03-19
It took a few restarts but finally disabling the ipv6 took effect.

---

