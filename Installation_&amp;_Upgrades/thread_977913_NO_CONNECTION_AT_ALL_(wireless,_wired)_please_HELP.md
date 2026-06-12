---
title: "NO CONNECTION AT ALL (wireless, wired) please HELP!!"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by vinz++ on 2008-11-10
hi. i'll make it short.
just did a fresh install of ubu 8.10. with hardy i don't remember having any problem to connect with wire. With intrepid it's being a nightmare.

I have a broadcom wireless card, i need to be connect to get it working, but wired connection doesn't work, only two green balls turning (besides mine), but then a error message. I'm lost. 

i post a couple of outputs..

lspci: 
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
lshw -C network:

*-network                
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:10:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: e 
       bus info: pci@0000:02:0e.0 
       logical name: eth0 
       version: 02 
       serial: 00:17:a4:d7:aa:78 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes 
  *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:1a:73:2d:7e:94 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 3 
       logical name: pan0 
       serial: 1e:a3:55:16:b1:37 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''' 


ifconfig: 

eth0      Link encap:Ethernet  HWaddr 00:17:a4:d7:aa:78   
          inet6 addr: fe80::217:a4ff:fed7:aa78/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2029 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:209793 (209.7 KB)  TX bytes:5336 (5.3 KB) 
          Interrupt:16  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:15500 (15.5 KB)  TX bytes:15500 (15.5 KB) 

''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
/etc/network/interfaces:

auto etho 
iface eth0 inet dhcp 
auto lo 
iface lo inet loopback 

''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
/etc/NetworkManager/nm-system-setting.conf
[main] 
plugins=ifupdown,keyfile 
 
[ifupdown] 
managed=true 

/etc/resolv.conf: i don't even have it.

Really hope someone can help me. 
thank's

---

