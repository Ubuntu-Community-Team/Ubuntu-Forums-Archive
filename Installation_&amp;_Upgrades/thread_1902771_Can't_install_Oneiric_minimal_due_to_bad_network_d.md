---
title: "Can't install Oneiric minimal due to bad network driver"
date: 2011-12-31
forum: Installation &amp; Upgrades
---

### Post by pumkinut on 2011-12-31
I'm trying to install Oneiric minimal (end result is an XBMC HTPC) onto my Biostar TH61 mini-ITX motherboard.  The install starts just fine, but it hangs quite a bit due to a network interface driver issue.

It seems, after doing a lot of searching, that the Realtek RTL8111E PHY is recognized by the installer, and the r8169 driver is used.  This is the problem, the 8169 driver is flaky and doesn't work all that well, whereas the r8168 driver works just fine.  

My question is, using the minimal install CD, can I build the correct module and insert it, during install, so that the install will complete?  If this works, I realize I'll have to rebuild/recompile the driver again and make everything work on the finished installation.  I'm just trying to find a way to install everything to begin with.

I'd use another NIC for the install, except the board only has a PCI-E x16 slot for video cards, and I just have PCI NICs.

---

