---
title: "Force install to use a specific network card during install"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by spoon103 on 2006-11-13
Hi,
     I'm trying to do a netboot / PXE install with Dapper and the machine has 3 seperate NICs in it.  The installer seems to randomly chose one of these cards to initilize during the install.  The problem is that only 2 of them are actually connected to the network with the TFTP and archive mirror server.  If there was a way to force the installer to choose a specific card that would be great.  Anyone have any ideas?

-Patrick

---

### Post by spoon103 on 2006-11-13
I found this kernel argument but i have a lot of machines to configure and I have no way of knowing which interface is the bum interface, anyone have anything better?

netcfg/choose_interface=eth1

---

