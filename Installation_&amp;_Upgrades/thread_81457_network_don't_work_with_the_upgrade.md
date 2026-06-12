---
title: "network don't work with the upgrade"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by jollyr0ger on 2005-10-24
hi. my network with the 5.04 were work fine good, but with the 5.10 it find the network hardware, but the lan don't work.

i think tah the dhcp don't work, but with the static ip don't work too.

how i can repair it?
else how i can downgrade the module of the networking?

thanks

---

### Post by misGnomer on 2005-10-24
Jollyr0ger,

Could you give details of your network, protocols used, your LAN hardware and what Ubuntu says about it?

How did you upgrade from Hoary to Breezy?

You could also check the Breezy networking forum to see if others have experienced similar problems, and perhaps found some answers already:

Ubuntu 5.10 --> Hardware Help --> Networking
[http://ubuntuforums.org/forumdisplay.php?f=101](http://ubuntuforums.org/forumdisplay.php?f=101)


Similar thing happened to me with Hoary just days ago. Probably caused by a security update (that probably also ships with Breezy), my PPPoE simply stopped working after a reboot and after much clueless troubleshooting I determined that my ASUS A7V880 mobos onboard Marvell Yukon Gigabit ethernet (which uses the sk98lin module) wasn't recogniced by Hoary (nor Breezy Live) any longer, although it still tested okay under the recent MCNLive ("jordaan") distro. I ended up disabling the onboard ethernet and installing a very cheap Realtek PCI controller which then worked fine under both Hoary and Breezy.

---

