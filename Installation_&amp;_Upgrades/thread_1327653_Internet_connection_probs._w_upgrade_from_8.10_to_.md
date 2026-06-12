---
title: "Internet connection probs. w/ upgrade from 8.10 to 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by flopwich on 2009-11-15
I just upgraded from Ubuntu 8.10 to 9.10.  My internet connections, which worked well in 8.10, now fail, both Ethernet and wireless.  They'll occasionally download a web page, but only after considerable time and will not do it again.  I can PING my mail server just fine with Network Tools and the System Testing utility says the wireless is working fine.  Also, I have Ubuntu as a dual boot on my Aspire One with Windows XP Home, which is able to access the wireless and ethernet just fine.

As a footnote, I tried to use Synaptic Package Manager to find some module I found mentioned in a thread for a similar problem, but after I type two characters into the search box, it would spontaneously close.

Anyway, I'd really appreciate some help with the connection problem.  I'm a noobie to Linux, so I'm over my depth here.  I found mention of the output of an "lcshw" command on another thread, so I provide it here in case it helps.

           [FONT=Arial, sans-serif][SIZE=2]*-network [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]description: Ethernet interface [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]vendor: Realtek Semiconductor Co., Ltd. [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]physical id: 0 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]bus info: pci@0000:02:00.0 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]logical name: eth0 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]version: 02 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]serial: 00:23:8b:80:8b:f6 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]width: 64 bits [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]capabilities: bus_master cap_list rom ethernet physical [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]resources: irq:28 ioport:3000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable) [/SIZE][/FONT] 
         [FONT=Arial, sans-serif][SIZE=2]*-pci:2 [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]description: PCI bridge [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]product: 82801G (ICH7 Family) PCI Express Port 3 [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]vendor: Intel Corporation [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]physical id: 1c.2 [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]bus info: pci@0000:00:1c.2 [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]version: 02 [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]width: 32 bits [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]capabilities: pci bus_master cap_list [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]configuration: driver=pcieport-driver [/SIZE][/FONT] 
              [FONT=Arial, sans-serif][SIZE=2]resources: irq:26 ioport:2000(size=4096) memory:55200000-562fffff ioport:52100000(size=16777216) [/SIZE][/FONT] 
            [FONT=Arial, sans-serif][SIZE=2]*-network [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]description: Wireless interface [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]product: AR5001 Wireless Network Adapter [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]vendor: Atheros Communications Inc. [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]physical id: 0 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]bus info: pci@0000:03:00.0 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]logical name: wmaster0 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]version: 01 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]serial: 00:24:2b:a7:ec:41 [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]width: 64 bits [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]capabilities: bus_master cap_list logical ethernet physical wireless [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]configuration: broadcast=yes driver=ath5k ip=192.168.2.100 latency=0 multicast=yes wireless=IEEE 802.11bg [/SIZE][/FONT] 
                 [FONT=Arial, sans-serif][SIZE=2]resources: irq:18 memory:55200000-5520ffff [/SIZE][/FONT]

---

