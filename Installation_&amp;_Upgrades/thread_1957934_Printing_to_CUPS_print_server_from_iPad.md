---
title: "Printing to CUPS print server from iPad"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by HellesAngel on 2012-04-13
Maybe someone can help - I have a headless server running Ubuntu 11.10 Server, clean install as LAMP server, with CUPS installed.  This prints successfully from other computers to the networked printer.  These computers are on the 192.168.1.xxx subnet.

The iPad is on the 192.168.3.xxx subnet and I have opened ports UDP 5353, TCP 3689 and TCP 631 between the two subnets.  From the iPad I can access the CUPS admin page on the server on [http://192.168.1.18:631](http://192.168.1.18:631).

On top of this I have followed the instructions [here ]("http://resteasy.info/index.php/3-get-airprint-working-on-ubuntu-printer-print-from-ipad-iphone-mac")to enable Apple AirPrint printing on the server but the problem is trying to get the iPad to discover the printer.  It always returns the rather unhelpful 'No AirPrint Printers Found', in true Apple style there are no logs.

The only meaningful error message is in the CUPS logs:[INDENT]Avahi client failed, closing client to allow a clean restart[/INDENT]This appears every time I restart avahi.  Anyone any ideas what's going wrong or how I can go about debugging?

---

### Post by HellesAngel on 2012-04-15
So, some progress of sorts, if I move the wireless devices to the same subnet as the print server then the iPad printer discovery works flawlessly.  This means the problem is actually an avahi/multicast/firewall problem. 

The solution seems to lie in  iptables and forwarding of packets across the subnets which means figuring this out.  Any hints?

---

### Post by wlraider70 on 2012-04-25
sorry for a bit of a side note. 

Did you have any permission issues?
I am trying to print from my Ipad and I am getting authentication issues.

---

### Post by melhe on 2013-02-06
Any progress on this? 

I have the same problem running 12.04 64bits. Purged and reinstalled avahi-daemon and cups to be sure but to no avail. I have similar setup on 12.10 and it works.

---

