---
title: "Ubuntu 5.10 Installation doesn't detect wireless NIC"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by Gargan on 2006-03-10
Hi,

I have a D-Link DWL-G510 Rev. B1 Wireless PCI NIC and it's not being detected during install... I thought that I read somewhere that the madwifi drivers were included with Ubuntu 5.10 and so this card should be detected during install.

Thanks,
Gargan

---

### Post by andlinux21 on 2006-03-11
have you tried using ndiswrapper to set your card up?

---

### Post by Gargan on 2006-03-11
How do I do this during the install so that my card is detected?

---

### Post by hotpurple on 2006-03-11
Do you know what chipset that card uses? If it's a broadcom chipset you will need to use ndiswrapper to set it up. You can't do this during setup, it will have to be done afterwards.

Chris

---

### Post by Gargan on 2006-03-11
I booted into a live cd of ubuntu 5.1 and ran lspci to get the chipset info.

Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)

I noticed that my other pci cards including my pci express vga card are also detected as unknown devices. I think this is why my wifi nic isn't being detected during install as it should be, since it has an atheros chipset and is supported under ubuntu 5.1, per other users experience with this card...

---

