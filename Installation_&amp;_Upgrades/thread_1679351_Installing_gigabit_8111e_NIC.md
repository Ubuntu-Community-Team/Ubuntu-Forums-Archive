---
title: "Installing gigabit 8111e NIC"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by balamquitze on 2011-01-31
Hi Everyone:

I have been trying to install the appropriate driver for my 8111e NIC (Realtek gigabit). I originally installed the proper driver from Realtek, and set up the "interfaces" file as follows:

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

# iface eth0 inet static
#    address 10.10.10.50
#    netmask 255.255.255.0
#    gateway 10.10.10.1

I also tried to set up the speed of the ethernet card using the "ethtool" as follows:
sudo ethtool -s eth0 speed 1000 duplex full autoneg off

When I check the result by typing "sudo ethtool eth0" I get the following:

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no

My problem is that when I reboot my computer, I do not get a connection to the internet. The only way for me to get connected is by going to the subdirectory where I have the 8111e driver and typing "sudo ./autorun.sh" twice. But if I reboot my computer I loose the network connection and when I type the command "sudo ifconfig -a", I get an output that indicates that the eth0 device did not pick up any IP address.

I am using Ubuntu 8.10 64-bit. I do not think this is the issue. I am hopping to find a way to set up the autodetection of the IP address permanently.

Also, the commands "ifdown eth0" or "ifup eth0" do not work. I have been checking many postings on the topic through the internet, but none of them has given me the proper solution.

Can any one suggests a solution to this problem.  Thank you in advance for your support.

Balamquitze

---

