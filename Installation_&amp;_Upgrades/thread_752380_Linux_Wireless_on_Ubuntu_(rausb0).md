---
title: "Linux Wireless on Ubuntu (rausb0)"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by damd79 on 2008-04-11
I'm trying to connect to an access point using a Linksys WUSB54G using Linux (Ubuntu 7.04 amd64)

I downloaded the driver, compiled and installed the driver, following the installation instructions.  The driver is installed successfully and the system recognizes the driver.  The problem is that when I type ifup rausb0, the dhclient attempts to connect, but no DHCPOFFERS are received.

I've ruled out the usual problems:

1. The access point itself is definitely working because a computer 2 feet away running WinXP has no problem connecting.
2. This problem is not related to encryption because the network is unsecure.
3. The access point is being detected.  If I type "iwlist rausb0 scanning" the access point shows up
4. I've correctly configured the /etc/network/interfaces file.  It is configured like:

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid belkin54g
auto rausb0

So basically everything seems to be in working order - but dhclient gets no DHCPOFFERS.  Any ideas, thoughts, suggestions as to what might be happening here?  Something I overlooked?

---

