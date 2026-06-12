---
title: "e1000e is turning on and off my network card repeatedly"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by borfig on 2011-03-06
I have:
> 00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
and it works perfectly with my current 2.6.37 kernel on the old Linux distribution I want to replace.
But when the Ubuntu 10.10 installation CD boots, it behaves very strange. here is the kernel log grep'ed e1000e, after I did a rmmod and modprobe, and tried to configure static IP:
> [  349.817899] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[  349.817902] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[  349.817936] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  349.817946] e1000e 0000:00:19.0: setting latency timer to 64
[  349.818280] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[  350.272711] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:67:7c:ff
[  350.272716] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[  350.272842] e1000e 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: ffffff-0ff
[  445.200187] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[  445.261295] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[  446.600867] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  446.600872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  450.100124] e1000e: eth0 NIC Link is Down
[  451.720866] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  451.720872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  456.130120] e1000e: eth0 NIC Link is Down
[  457.770865] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  457.770870] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  459.000120] e1000e: eth0 NIC Link is Down
[  460.740915] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  460.740918] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  466.980121] e1000e: eth0 NIC Link is Down
[  468.600867] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  468.600872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  468.840119] e1000e: eth0 NIC Link is Down
[  470.442116] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  470.442122] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  473.300120] e1000e: eth0 NIC Link is Down
[  474.942121] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX                                                                                                
[  474.942126] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO                                                                                                               
[  476.070119] e1000e: eth0 NIC Link is Down                                                                                                                                        
[  477.680922] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX                                                                                                
[  477.680927] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO                                                                                                               
[  484.080121] e1000e: eth0 NIC Link is Down                                                                                                                                        
[  485.830866] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX                                                                                                
[  485.830871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO                                                                                                               
[  486.440119] e1000e: eth0 NIC Link is Down                                                                                                                                        
[  488.150866] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX                                                                                                
[  488.150872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO                                                                                                               
[  490.030120] e1000e: eth0 NIC Link is Down                                                                                                                                        
[  491.720866] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX                                                                                                
[  491.720871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO                                                                                                               

Same thing happens with dhcp.
I won't have Internet access after install Ubuntu 10.10 and that's a shame :(
How do I fix this?

---

