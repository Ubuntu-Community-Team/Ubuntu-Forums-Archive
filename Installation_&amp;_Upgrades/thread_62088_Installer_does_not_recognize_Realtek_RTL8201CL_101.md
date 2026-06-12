---
title: "Installer does not recognize Realtek RTL8201CL 10/100 onboard LAN"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by DarkRider on 2005-09-03
Hello,
Installer does not recognize Realtek RTL8201CL 10/100 onboard LAN, and because of that after intallation no network connection exist. Any help appreciated ! 

Othervise UBUNTU is running fine in my machine, but just can not move to  using it fully without network connections. I Guess I need to go back to WINDOWS if this can't be solved ??
THX !

lspci and lspci -n results here:
0000:00:00.0 Host bridge: ALi Corporation: Unknown device 1695 
0000:00:01.0 PCI bridge: ALi Corporation: Unknown device 524b 
0000:00:02.0 PCI bridge: ALi Corporation: Unknown device 524c 
0000:00:04.0 Host bridge: ALi Corporation: Unknown device 1689 
0000:00:05.0 PCI bridge: ALi Corporation: Unknown device 5246 
0000:00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge 
0000:00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70) 
0000:00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU] 
0000:00:08.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Cont roller Aud Device (rev 20) 
0000:00: 11.0 Ethernet controller: ALi Corporation: Unknown device 5263 (rev 40) 
0000:00: 12.0 IDE interface: ALi Corporation M5229 IDE (rev c7) 
0000:00:12.1 Unknown mass storage controller: ALi Corporation: Unknown device 5289 (rev 10)
OOOO:00:13.0-USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
0000:00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
0000:00:13.2 USB Controller: ALi Corporation USB 1.1 COI!troller (rev 03) 
0000:00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) 
0000:00: 18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00: 18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:03:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0042 (rev a1) 

jan@ubuntulspci -n 
0000:00:00.00600: 10b9:1695 
0000;00;01.00604: 10b9:524b 
0000:00:02.00604: 10b9:524c 
0000:00:04.00600: 10b9:1689 
0000:00:05.00604: 10b9:5246
0000:00:06.00604: 10b9:5249 
0000:00:07.00601: 10b9:1563 (rev 70) 
0000:00:07.10680: 10b9:7101 
0000:00:08.00401: 10b9:5455 (rev 20) 
0000:00:11.00200: 10b9:5263 (rev 40) 
0000:00:12.00l0l: 10b9:5229 (rev c7) 
0000:00:12.10180: 10b9:5289 (rev 10) 
0000:00:13.00c03: 10b9:5237 (rev 03) 
0000:00:13.10c03: 10b9:5237 (rev 03) 
0000:00:13.20c03: 10b9:5237 (rev 03) 
0000:00:13.3Oc03: 10b9:5239 (rev 01) 
0000:00:18.00600: 1022:1100 
0000:00:18.10600: 1022:1101 
0000:00:18.20600: 1022:1102 
0000:00:18.30600: 1022:1103 
0000.03.00.00300: 10de:0042 (rev a1)

---

