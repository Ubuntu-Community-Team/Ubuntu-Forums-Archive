---
title: "WPC54G and ndiswrapper"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by firemagius on 2005-05-19
Just thought I would post my success with the WPC54G and ndiswrapper.  I tried the wpc54g drivers, version 1.3, 2.0, and whatever came on the CD when I bought the card.  I could not get it to work, even though those drivers worked under Gentoo.  (ndiswrapper would never see the hardware.)

So, I checked lspci and saw:

0000:03:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

And I went to

[ftp://ftp.support.acer-euro.com/notebook/aspire_1360/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_1360/driver/80211g.zip)

and pulled down those drivers.  After a "ndiswrapper -i neti2220.inf"  ... viola!  Now my laptop sees the hardware.  "ndiswrapper -m" and moving on.  I added wlan0 to my /etc/network/interfaces file and "ndiswrapper" to /etc/modules and I was ready to go.

My interfaces file minus comments:

auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0
        map wlan0

iface eth0 inet dhcp
iface wlan0 inet dhcp

---

### Post by d00m on 2006-01-05
That driver works perfect!!!!! Thank you, i've been trying to get my WPC54Gv4 up with no success until now.

---

### Post by K2712 on 2006-01-06
I have been trying forever to bring my WpC54Gv4 up since I upgraded to Breezy.  I have the driver installed, and ndiswrapper -l shows driver and hardware present, but when i type iwconfig this is what I get:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

My /etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
	map wlan0

# The primary network interface
iface eth0 inet dhcp
iface wlan0 inet dhcp

When I try sudo ifup wlan0:

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.

I've read all the wiki's and searched the forums and I cnn't figure out what the problem is.  If anybody has any ideas I would really appreciate it.

---

### Post by d00m on 2006-01-06
I had the same issue with iwconfig until I rebooted. 

I also never modified the interfaces file, but that's just what worked for me :)

---

