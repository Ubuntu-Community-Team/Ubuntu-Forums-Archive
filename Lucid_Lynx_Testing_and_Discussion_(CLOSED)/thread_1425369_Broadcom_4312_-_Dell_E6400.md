---
title: "Broadcom 4312 - Dell E6400"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gunksta on 2010-03-09
I installed 10.04 fresh @ Alpha 3. Everything, but the wireless worked out of the box.

System -- Dell Latitude E6400
Wifi Card -- Broadcom 4312
Version -- Kubuntu (not that I think it matters here)

I have tried using the b43 driver with the firmware installed by fwcutter, but it rapidly freezes up my system with DMA errors. I has to stop and reload the driver once every few seconds, rendering the system unusable.

This annoyed me, and I removed and blacklisted the b43 driver. This eliminated the system-hangs, but rendered my wireless card rather useless.

So I opened up the proprietary hardware dialog and proceeded to let it install/set up the proprietary STA driver. After doing so, my wifi LED is lit, but I still don't have wireless.

Here's the output of some useful stuff that I've been staring at. Perhaps someone else will see something that I don't.

```
lsmod|grep -e b43 -e ssb -e wl -e ndiswrapper
```

wl                   1965192  0 
lib80211                6119  2 lib80211_crypt_tkip,wl


```
dmesg|grep wl
```

[    7.945682] wl: module license 'MIXED/Proprietary' taints kernel.
[    7.950545] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.950558] wl 0000:0c:00.0: setting latency timer to 64


```
sudo lshw -C network
```

*-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:a7:50:b7
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.7-7 ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation                                                                                                                              
       physical id: 0                                                                                                                                            
       bus info: pci@0000:0c:00.0                                                                                                                                
       logical name: eth1                                                                                                                                        
       version: 01                                                                                                                                               
       serial: c4:17:fe:64:25:4c                                                                                                                                 
       width: 64 bits                                                                                                                                            
       clock: 33MHz                                                                                                                                              
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                                                                            
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg                                           
       resources: irq:17 memory:f69fc000-f69fffff                                                                                                                
  *-network DISABLED                                                                                                                                             
       description: Ethernet interface                                                                                                                           
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


```
iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.



(Yes, I do have virtual box installed)

I have Googled this to pieces and I haven't seen anything that can make this wireless card operate correctly. Any ideas?

---

### Post by zombiepig on 2010-03-09
Try installing bcmwl-kernel-source. That's always worked for me in the past. ;)

---

### Post by gunksta on 2010-03-09
I should have been more clear -- That is what I have done. When you install the STA drivers via the GUI you install the bcmwl-kernel-source package. 

The bcmwl-kernel-source package installs the wl driver. Which , as you can see in my original post, is definitely installed and active on my system.

I have blacklisted the b43 driver and you can see in my original post that it is not loaded in my kernel.

But, although my Wifi light is on, I can't see my local network. I know it's working because my girlfriend is currently watching YouTube on this network and I'm closer to the Wireless Access Point than she is (I'm roughly 5 feet from it).

Ideas are definitely appreciated.

---

### Post by Trespasser on 2010-03-09
On a fresh install I've gotten in the habit of individually installing dkms, fakeroot, patch, and then the bcmwl-kernel-source package from the live-cd to get my wireless working. I tend to have trouble if I try it any other way.

Later...

---

### Post by gunksta on 2010-03-09
I've tried to reinstall those packages and no change.

---

### Post by petejk on 2010-03-09
gunksta - 

I have that exact same problem from time to time.

I have a bcm4328 chip using the bcmwl-kernel-source driver.
iwconfig gives the same output as you.

try editing resolv.conf

[B]sudo gedit /etc/resolv.conf

[/B]comment out anything there currently, and add opendns addresses

[B]nameserver 208.67.222.222 
nameserver 208.67.220.220[/B]

then reboot. Did the trick for me.

Pete

---

### Post by gunksta on 2010-03-09
Thanks petejk

I committed the changes, but now I'm at work and we don't have any wireless networks here. There's a network across the street that we can sometimes see but the fact that I can't see it right now means all of nothing. I may not know for sure if this worked until I get home.

---

### Post by gunksta on 2010-03-10
No dice. I still see absolutely nothing.

---

### Post by cariboo on 2010-03-10
Adding DNS addresses to /etc/resolv.conf only works if you never reboot, as it is overwritten by network-manager, If you want to change DNS server addresses do it using network-manager, you can set them on the IPv4 tab.

---

### Post by gunksta on 2010-03-10
I'm sort of hoping this or the b43 driver will get fixed in an update or someone here will have some idea for why the STA driver won't work.

---

### Post by gunksta on 2010-03-12
Don't know how or why -- But now I can see wireless networks. In fact, the wireless in this system appears to work much better than the wireless in my old system.

I just wanted to thank everyone who offered ideas.

Thanks

---

