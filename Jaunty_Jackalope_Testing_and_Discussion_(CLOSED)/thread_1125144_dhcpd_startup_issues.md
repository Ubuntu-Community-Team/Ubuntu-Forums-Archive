---
title: "dhcpd startup issues"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hagan on 2009-04-14
Hello,
I have a dhcp3-server installed and it works perfect when I start it in a running system. But at start-up it does not come up as expected. The interesting lines out of syslog are below. It seems dhcpd is starting before the network manager and therefore the interface which dhcpd should listen on is not configured when it starts up (it is eth1 which I set with a static IP in the network manager). Am I doing something wrong here, or should I report a bug?

Apr 14 10:10:04 nuwen dhcpd: No subnet declaration for eth1 (0.0.0.0).
Apr 14 10:10:04 nuwen dhcpd: ** Ignoring requests on eth1.  If this is not what
Apr 14 10:10:04 nuwen dhcpd:    you want, please write a subnet declaration
Apr 14 10:10:04 nuwen dhcpd:    in your dhcpd.conf file for the network segment
Apr 14 10:10:04 nuwen dhcpd:    to which interface eth1 is attached. **
Apr 14 10:10:04 nuwen dhcpd: 
Apr 14 10:10:04 nuwen dhcpd: 
Apr 14 10:10:04 nuwen dhcpd: Not configured to listen on any interfaces!


Apr 14 10:10:04  ... some more not related stuff ...


Apr 14 10:10:06 nuwen NetworkManager: <info>  starting... 
Apr 14 10:10:06 nuwen NetworkManager: <info>  (eth1): new Ethernet device (driver: 'skge') 
Apr 14 10:10:06 nuwen NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_18_f3_9e_31_01 
Apr 14 10:10:06 nuwen NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2') 
Apr 14 10:10:06 nuwen NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_18_f3_9e_51_2b 
Apr 14 10:10:06 nuwen NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Apr 14 10:10:06 nuwen NetworkManager: <info>  Trying to start the supplicant... 
Apr 14 10:10:06 nuwen NetworkManager: <info>  Trying to start the system settings daemon...

...

Apr 14 10:10:12 nuwen NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...

---

### Post by Anthon on 2009-04-14
It looks like dhcp is started before your ethernet card is active.
You can change this by the numbers XY in the link in /etc/rcZ.d/SXYdhcp3-server
(as shown by doing
  ls /etc/rc?.d/S*dhcp3-server
The S after the last slash stands for start). 
That number XY should be greater thanwhat you get with
ls -l /etc/rc?.d/S*network*

---

### Post by hagan on 2009-04-15
It is actually the Network-Manager configuring the interfaces, since i am on a Desktop install. And you are correct, that dhcp is startet before the Networkmanager which is the problem. But even if I put it behind Network-Manager in the start-up queue, Network-Manager takes so long dhcp is still to early.

---

