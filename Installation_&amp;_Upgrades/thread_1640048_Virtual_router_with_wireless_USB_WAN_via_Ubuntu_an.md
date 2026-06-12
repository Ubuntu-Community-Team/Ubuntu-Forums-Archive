---
title: "Virtual router with wireless USB WAN via Ubuntu and VMWare?"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by greennewb on 2010-12-07
I bought a USB wireless card that supposedly has Linux drivers for it (haven't tried it yet).  Assume, for the moment, that it does work fine.  I also have a license of VMWare Workstation 7.  I also have a laptop running Windows 7.  The laptop has both a wired and an embedded wireless card.  I plan on disabling the latter.

Here's what I want to do:  Set up a virtual router on the Windows 7 laptop using VMWare and some flavor of Linux and pass all network traffic through the virtual router.

Here's how I envision a packet traveling out to the wireless network:  Packet -> embedded NIC -> VMWare virtual NIC (bridged*) -> VMWare machine -> Linux picks up the packet coming in and, emulating a router, performs NAT translation -> Modified packet sent out to the wireless card (via VMWare's USB passthrough feature).

* Is that even possible? Or will Windows send packets directly to  the VMWare virtual NIC as it will be the only active network device?

I'm thinking Ubuntu for the host OS because it will have the greatest chance of recognizing the USB wireless card without fiddling around too much.  However, I'm not sure how to turn Ubuntu into a router where a USB wireless card can be treated as the WAN endpoint and an Ethernet NIC is the LAN endpoint.  This is just an experiment at the moment, so suggestions are welcome.

---

