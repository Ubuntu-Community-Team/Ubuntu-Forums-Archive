---
title: "New Installation of Ubuntu on laptop, wireless/internet connectivity assistance"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by bizdcrawl on 2008-08-04
I just installed the latest version of Ubuntu on my laptop as a partition. Everything is fine and peachy. I am a totally satisfied customer so far.

My next project is to get the wired/wireless internet working and obtain all the necessary hardware drivers. I have a Broadcom Netlink BCM5787M Ethernet controller and a BCM4312 network controller. But, by default, my computer is not picking up either connection. :(

so, what should be my next logical step to get the internet working and get my drivers in place. Any links, suggestions would be greatly awesome.

Thank You.

---

### Post by bizdcrawl on 2008-08-04
I tried "lshw -C network" and the network card had no driver description. Umm...I thought this version of Ubuntu came with driver support for Broadcom 43xx cards :confused:

So, now that I know I dont have network drivers, can some one suggest me a link on how to obtain and install the drivers? The ndiswrapper thingy

Please... :sad:

---

### Post by ezsurfer on 2008-08-04
I merely went to administration, found the networking tab, followed it, finally got my security setup correct, and it picked up the wireless right away.

System - Administration - Networking...

---

### Post by bizdcrawl on 2008-08-04
hey,

I went into system-administration-network and instead of enable roaming I had "enable this connection" option. I checked it, put in my network name and the network password and set it to DHCP. But as said earlier, my laptop doesnt show any driver per se for the network card. I'd imagine it should say or mention ndiswrapper details??

---

### Post by bizdcrawl on 2008-08-04
I cant wait to get this thing working :tongue:

---

### Post by bizdcrawl on 2008-08-04
here's what sudo lshw -C network said

*-network               
       description: Ethernet interface 
       product: NetLink BCM5787M Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:10:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1a:4b:8d:59:bd 
       size: 100MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s 
  *-network 
       description: Network controller 
       product: BCM4312 802.11a/b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:30:00.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:00:00:1a:73:e3 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by ezsurfer on 2008-08-08
I checked it again, because it was harder to set up this time.  Still, eventually, I kept bouncing back and forth between it and network tools so I could ping the router (192.168.1.1) on most systems.

Once it pinged, it worked fine.  Not sure why, but the first 3 or so times I set it up it did not allow the connection.  

Finally went back to exactly what I wrote you, set the password up in openoffice so i could verify the WEP key wasn't getting set wrong, and pasted it in, and it locked right in and pinged, so now it's back on wireless.

---

