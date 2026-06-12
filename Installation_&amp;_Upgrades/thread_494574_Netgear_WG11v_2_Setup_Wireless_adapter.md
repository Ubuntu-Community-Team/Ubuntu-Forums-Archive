---
title: "Netgear WG11v 2 Setup Wireless adapter"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by xtroid2k on 2007-07-07
Hi Guys,

Ok I installed Ubuntu 7.04 on my Dell inspiron 1150. 

I did my research and bought a netgear WG511 v2, as that seems to be somewhat compatbile with linux and if not, well just out $20

I installed it in the pcmcia slot. and here is what I get when I type (lspci -v | less), I just copied the wireless section

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
Subsystem: Netgear WG511 v2 54MBit/ Wireless PC-Card
Flags: 66MHz, medium devsel, IRQ 11
Memory at f8000000 (32-bit, non-prefetchable) [disabled] [size=64K] 
Memory at f8010000 (32-bit, non-prefetchable) [disabled] [size=64K]
Capabilities: <access denied>

I need help configuring it, as it is not showing up in the list of devices to configure in the network section under administration.

I tried looking for various reasons on different forums. I even tried ndiswrapper, however after installing the .inf file from the cd it still doesn't work.

Any help would be appreciated 

thanks

xtroid2k

---

### Post by xtroid2k on 2007-07-08
ok

installed useing linuxant

---

