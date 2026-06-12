---
title: "Network Manager"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by thrillhouse on 2006-06-02
Hi, I just upgraded from Breezy on my Thinkpad T41.  I noticed that my Network-Manager doesn't work nearly as well.  In Breezy, I could just open my laptop and it would see if it could connect to an AP.  Now, if I am wired, I get an internet connection.  If I unplug my cord and click on the network-manager applet,all it says under it is “wired connection,” but it is grayed out so I can't click on it.  In Breezy, it would give me some options about connecting to other networks and how I wanted to connected to them (not to mention a list of available access points to connect to).  Any advise would be terrific.  If you need any more information, just ask.  Below is the output of my lspci.
0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

### Post by vbatts on 2006-06-02
i've had similar issues, 
the only way to connect is through Admin -> Networking
or
iwconfig, 
and 
the only way to find availible wireless is '$ iwlist ra0 scan'

i am a kde person and so far i've been experimenting with ubuntu's gnome, and haven't installed kde anything yet. but i'm familiar with the network tools within kde like kinternet. 

last night at the dapper release party here in birmingham,al i had a difficult time even attaching to panera bread's wifi, once online i apt-get'ed network-manager and network-manager-gnome, but it only sees 'wired connections', enabling wireless or viewing wireless networks isn't even availible. and Applications -> Internet -> Network Selector isn't of any use either.

is this an issue with the ralink being 'ra0' instead of 'wlan0' or what?

vb

---

### Post by bjchamb on 2006-06-02
I had a similar problem.  As far as I can tell, the issue is that the built in network management that comes with Ubuntu interferes witch the Network Manager, and prevents it from getting control of the wireless.  The solution is to open up /etc/network/interfaces, and make sure that the part dealing with your wireless interface looks like the following:

auto <interface>
iface <interface> inet dhcp

(Where <interface> is your wireless interface).

Any other lines, such as wireless configuration options, should be either deleted or commented out (by putting a # at the start of the line).  This should make it so that the network manager is able to control your wireless interface.

Hope that helps.

---

### Post by thrillhouse on 2006-06-02
Awesome!!!  Works just like before.  Thanks alot!!!!!:D   Have a good weekend!

---

