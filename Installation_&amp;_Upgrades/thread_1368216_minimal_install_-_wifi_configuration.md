---
title: "minimal install - wifi configuration"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by mailman1175 on 2009-12-30
It's me again, Margaret&#8230; :)

I decided to try to build my own Ubuntu from a minimal install. Since I have a working Karmic (UNR) install on another partition on my machine (an Acer Aspire One 110L), I figured a minimal Karmic image was the best place to start.

The netbook remix installation went by without a hitch: wireless was working out of the box. I was hopeful (though probably as much out of ignorance about the process as any anything) that the minimal install would recognize and configure my wireless hardware correctly. It does recognize the wireless hardware. But it's not working.

```
$ sudo lshw -C network
[snip]
*-network
           description: Wireless interface
           product: AR5001 Wireless Network Adapter
           vendor: Atheros Communications Inc.
           physical id: 0
           bus info: pci@0000:03:00.0
           logical name: wmaster0
           version: 01
           serial: 00:22:69:21:09:a3
           width: 64 bits
           clock: 33MHz
           capabilites: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
           configuration: broadcast=yet driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
           resources: irq:18 memory:35200000- 3520ffff
$ 
```

This shows my wireless card is at least being recognized. This is all exactly the same output that I get in the working KarmicUNR install.

Getting wifi going on this machine has been a pain in the keister with every installation I've done, with the notable exception of the Karmic UNR install. I had working wireless on a Hardy install, using madwifi drivers. I couldn't get madwifi to work for me in the brief attempt I made with Crunchbang 9.04. All the troubleshooting threads I've poked through on this forum, and the couple of Ubuntu wiki pages on network troubleshooting&#8230; well, I leave them not knowing much more than I did before I started searching. They're either too specific (in the case of the threads here) or too general/outdated (in the case of the wiki pages).

So, if y'all can help me get wireless up and running, I'd appreciate it. I'd love to learn a bit more about how the networking pieces work, and how to troubleshoot when they're not.

TIA

Edited to add: I've installed wicd, and I've run wicd-client&#8230;

```
$ wicd-client
Importing pynotify failed, notifications disabled.
Has notifications support False
Loading&#8230;
Connecting to daemon&#8230;
Connected.
Done loading.
```

And that's it. No GUI, but that may be because there's something I've yet to install. I don't have a task bar yet in Openbox, so I don't have any graphical indication for what it's doing.

---

### Post by mailman1175 on 2009-12-30
This works... sort of. The connection seems to drop out after a little while.

Ideas?

```
$ sudo iwconfig wlan0 essid home
[sudo] password for jeff: 
jeff@Karma:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:22:69:21:09:a3
Sending on   LPF/wlan0/00:22:69:21:09:a3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.2.4 from 192.168.2.1
DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.4 from 192.168.2.1
bound to 192.168.2.4 -- renewal in 885284262 seconds.

```

---

### Post by mailman1175 on 2009-12-30
Ok, I think I've got it solved. I added a tint2 panel, so I can actually use the applet. It finds the network, gives me the option to connect automatically. Rebooted, and it connected. So, unless I continue getting weird disconnect behavior, I'm going to call it good.

I guess I should thank a forum sponsor for giving me a place to verbally process, or something. :rolleyes:

---

