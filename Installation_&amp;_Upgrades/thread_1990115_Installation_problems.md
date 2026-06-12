---
title: "Installation problems"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by Calorca on 2012-05-29
Hello everybody!!

I am absolutely new with Linux. Until now I always used Windows, but I wanted give Ubuntu a try.

I tried to install the newest version, but my HP couldn't coop so I had to install the 9.04 version that I had.  
Now my problem is I can't connect to the internet, whether LAN nor Wireless.:( I search for solutions and found a way to install the Windows driver, which I did, but without any success. 
Can someone give me a clue what to do?

Thanks in advance!:P

---

### Post by dino99 on 2012-05-29
the first thing to try: is the livecd (liveusb) works , specially the internet ?

then its a good idea to talk a bit more than just "HP" about your system.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

---

### Post by Calorca on 2012-05-29
Hello
Thanks for the fast answer.
I tried to do it with the usb live version, but my laptop did'nt recognize it. When I entered the boot menu there was only the notebooks hd.
I have a HP touchsmart tm2 with touchscreen. And until now I think the main problem is the internet. The wireless adapter doesn't work properly and when I plug in the LAN cable and try to connect with the router by browser it doesn't answer.
Tomorrow I'll try doing the partitions you suggested.

---

### Post by garvinrick4 on 2012-05-29
Post your cards for network so users can help you with your internet connection;
Open a terminal "ctrl/alt/t" all at same time and copy and paste this below. Copy and paste results of below to this thread.

```
sudo lshw -C network
```

---

### Post by Calorca on 2012-05-30
```
sudo lshw -C network
```
That's what I've got:

```
*-network                
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 03 
       serial: 1c:c1:de:8f:92:a0 
       size: 10MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s 

  *-network UNCLAIMED 
       description: Network controller 
       product: Broadcom Corporation 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 

  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: f6:17:4c:f0:24:48 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

