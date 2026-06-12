---
title: "Warty -&gt; Hoary: now no sign of network"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by nathanj on 2005-04-14
I've just upgraded to 5.04 following the steps in the release notes. Maybe a bad move to move to a needier system, but a memory upgrade for this old Thinkpad T20 should help and if it's still sluggish, I'll look into using XFCE. Install went okay, using packages from the CD and some from the Internet.

Now, however, I have no sign of the network. On Warty, the machine grabbed an IP via DHCP at startup. I don't believe this is happening now.

My first thought: go to System -> Administration -> Networking, where I used to see the Ethernet interface. Instead, I see an unconfigured "Modem connection" with a Properties button. Activate and Deactivate greyed out and no Add button as suggested in the help screens.

Any suggestions on where to turn next?

---

### Post by DoubleDangerClub on 2005-04-17
I'm also having a similar problem, when I go to the Network Settings, I can't add my wireless connection now.  Any ideas?

DDC

---

### Post by nathanj on 2005-04-20
I guess the question should be "where can I find information on getting Ubuntu to recognise my network card?".

It seems that is the only reason that the network is not listed in System -> Administration -> Networking, is that the card is not recognised.

Under Warty, it would either instantly find the network and get details via DHCP, or (if the cable was unplugged) sit for two minutes at the "Configuring Network Interfaces" during startup, trying to find the network.

Under Hoary, "Configuring Network Interfaces" just flashes past and no network connection is established.

---

