---
title: "Install over network: Can't get TFTP working"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2010-01-17
I am trying to install Xubuntu 9.10 on a very old notebook (details below) but I keep getting stuck at the TFTP part.

The notebook is set to PXE boot, and it does, first getting assigned an IP address by my router.

After that step, I see a "TFTP..." message, which eventually changes to the error message "PXE-E32: TFTP open timeout".  After that happens several times, the notebook gives up & tries to boot off the hard drive.

The hardware involved:

Ubuntu 9.10 desktop machine (server): This is the machine I want to use as the server for the Xubuntu install over the local network. Its IP address is 192.168.1.20.

Linksys BEFSX41 router: local IP address 192.168.1.1 (usual for a router). Runs a DHCP server for the LAN.

Compaq Presario 710 (client): This is the machine I want to install Xubuntu on. According to its PXE booting screen, it has a Realtek RTL8139 v2.11 network adapter, with MAC 00:08:02:2C:70:7C.

Strangely, I have no problem getting TFTP to work under Windows XP, it's just under Ubuntu 9.10 that it refuses to work.  When running Win XP, I use a TFTP server called TFTP32.  TFTP32 and the notebook's PXE hardware see each other right away, and presto, I have an Ubuntu install screen.

I tried the network install tutorial here ([https://wiki.ubuntu.com/Installation/LocalNet](https://wiki.ubuntu.com/Installation/LocalNet)), among others, but it doesn't work.

UPDATE:

OK it seems that having my router run its own DHCP server was somehow causing a problem.  As soon as I stopped the router's DHCP server, and set up a DHCP service on my Ubuntu 9.10 machine as specified in this guide ([https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)), then restarted the target notebook, POOF!  The Presario 710 came right up with an Ubuntu install screen.

Now I have to figure out how to serve the Xubuntu 9.10 desktop install CD to the notebook over the LAN.  But I think that will be an easy problem to fix.

---

