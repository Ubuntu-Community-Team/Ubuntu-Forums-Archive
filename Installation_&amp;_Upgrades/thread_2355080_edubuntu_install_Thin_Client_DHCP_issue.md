---
title: "edubuntu install Thin Client DHCP issue"
date: 2017-03-09
forum: Installation &amp; Upgrades
---

### Post by dmamt on 2017-03-09
I'm not sure how to state this issue. However, after a final breakthrough with installing Edubuntu LTS on an HP Z800 Workstation. I am now unable to get an HP Elitebook to boot as a thin client.

The HP Elitebook (potential thin client) is a completely wiped system, there is no bootable OS on it. I would like to use the Edubuntu LTS so that it boots from the server I just installed. 

My setup is as such -

Internet modem - netgear router - cisco switch - Edubuntu LTS (HP Z800 Workstation)

The Thin Client I setup will be connected to the switch. This was exactly like the diagram in the One-NIC example given by the installation guide. However, when I change the BIOS of the Thin Client so that it boots through PXE - Etherboot it looks for DHCP..... but receives  nothing. I have to imagine that this is because it is looking to the router which is a DHCP server.

One might tell me to not have the router be a DHCP server... but I want other devices to access the internet through it without having to use the Edubuntu LTS as it will be turned off when the Computer Lab is not in use.

So How to I have the router continue to operate as a DHCP server and allow the Edubuntu LTS to be the DHCP server for just the thin clients in the computer lab. As the thin clients need the Edubuntu LTS inorder to boot an OS.

Thanks

---

