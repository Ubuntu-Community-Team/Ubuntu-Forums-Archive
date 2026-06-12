---
title: "Studio 8.04 install: no wired router connection during/after"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by swguy on 2008-06-11
A fresh install of Ubuntu Studio Alternate 8.04 i386 on a Toshiba Satellite A205-SP5813 works perfectly except for internet connections. A wired DHCP connection was not detected during or after install if the cable was connected to the TP-LINK router.  When the cable was connected directly to the cable modem on a re-install, the DHCP connection worked during and after install.

I found out that the Network Manager was not installed, so network-manager and network-manager-gnome were installed via Synaptic Package Manager (SPN) and roaming was enabled for the wired connection. This resulted in the same behavior as before: no router connection, only cable modem connection.

The connection information with a router connection shows all zeros for IP address, broadcast address, subnet mask, default route, primary DNS, and secondary DNS. A ping of 192.168.1.1 returned zero packets.

Conversely, when running _from_ the Live CD the router connection worked perfectly as Network Manager was already installed from the beginning.  An install from the Live CD also worked. Thus, no hardware issues are present.

I have had the same issue with both Alternate 8.04 i386 and Alternate 8.04 AMD64 installs.  Only the Live CD versions work out of the box.  Studio only comes in the Alternate form.

What do I need to change to get NM to access the router?

---

### Post by swguy on 2008-06-11
Hi everyone,

The above issue applies to **ALL** alternate install variants, not just the Studio distro. I can't believe I'm the only one with this issue in Hardy.  Maybe it's an old issue to many of you, but I can't seem to find an answer via Google.  Any help would be appreciated. 

Thanks.

---

