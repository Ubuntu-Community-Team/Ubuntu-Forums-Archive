---
title: "Alternate 8.04 install: no wired DHCP router connection"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by swguy on 2008-06-11
A fresh install of ***Ubuntu Studio Alternate 8.04 i386*** on a Toshiba Satellite A205-SP5813 works perfectly except for internet connections. A wired **DHCP** connection was _not_ detected during or after install if the cable was connected to the **TP-LINK** router.  When the cable was connected directly to the cable modem on a re-install, the **DHCP** connection worked during and after install.

I found out that *Network Manager* was not installed, so *network-manager* and *network-manager-gnome* were installed via *Synaptic Package Manager (SPM)* and roaming was enabled for the wired connection. This resulted in the same behavior as before: no router connection, only cable modem connection.

The connection information with a router connection shows all zeros for IP address, broadcast address, subnet mask, default route, primary DNS, and secondary DNS. A ping of 192.168.1.1 returned zero packets.

Conversely, when running _from_ the **Live CD** the router connection worked perfectly as *Network Manager* was already installed from the beginning.  An install from the **Live CD** also worked. Thus, no hardware issues are present.

I have had the same issue with both ***Alternate 8.04 i386*** and ***Alternate 8.04 AMD64*** installs.  I tried the standard guided install, LVM install, and LVM encrypted install.  Only the **Live CD** versions work out of the box.  *Studio* only comes in the Alternate form; no choice here.

What do I need to change to get NM to access the router?

---

### Post by Builder on 2008-07-04
I had a similar experience to that of swguy (he was much more detailed, I'm just supporting evidence).  There were no problems with an Alternate Ubuntu 8.04 install, up & running fine, then I couldn't seem to download updates (in spite of having been told how many there were).  I then went for the Edubuntu additions, and some of those must have been net-based packages as well, they didn't download.  Eventually I located this thread, and began to realize the extent of the problem.

Of course, there _is_ an "alternate" methodology to the LTSP part (just install the package after a Desktop install), but I see no way to do also / instead do an encrypted LVM as download (well, OK, no _easy_ way, there's undoubtedly a hard way).

TIA for comments.

---

