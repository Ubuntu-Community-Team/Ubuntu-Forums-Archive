---
title: "Intrepid upgrade broke Intel 3945AGB."
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Akegata on 2008-11-01
I just upgraded my laptop (a Thinkpad X60s) to Intrepid, and everything seems to work fine, except the WLAN, which sadly makes the laptop kind of pointless. :)

After the upgrade, I can still associate the WLAN card, a Intel 3945AGB card, to my access point, but I can't get an IP address from the DHCP server.
Pluging in the wired connection and running dhclient eth0 gives me an IP address on the wired card just fine.

I don't really know where to look. I'm running fluxbox, and just made an alias called "wlan" that connects to the AP using iwconfig.
I tried firing up Gnome, but the network icon says there are no network connections, even when the wired connection is up and running, so no clues there.

Any help would be highly appreciated.

Edit: I just installed wicd, and now I get an IP address just fine. Awesome application.

---

