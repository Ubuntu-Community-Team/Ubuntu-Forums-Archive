---
title: "Network manager seems disabled"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zooounds on 2008-10-07
Look at the screenshot.

Network manager says "unconnected" and all connections are greyed out.

I have probably been tweaking something in my Hardy installation before upgrading. Is threr any way to make it right again?

My network works fine, it's just network manager that doesn't see this.

---

### Post by executor on 2008-10-07
try this, open   sudo gedit /etc/NetworkManager/nm-system-settings.conf

it the [ifupdown] managed=false set it to true.

---

### Post by zooounds on 2008-10-07
> **executor said:**
> try this, open   sudo gedit /etc/NetworkManager/nm-system-settings.conf

it the [ifupdown] managed=false set it to true.

It was set to false but it didn't solve it.

If think bug 279262 could be it:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262)

Also if I try to edit my network connection (right click->settings etc) the network-manager will crash.

Something is really wrong.

---

### Post by Locke_99GS on 2008-10-07
I had the same problem.

Everything seemed to work - except FireFox. Everything else would connect as normal (Pidgin, apt-get, MPD, Epiphany).

In this state, Network Manager was about useless. Attempts to edit eth0 through nm-applet resulted in an error, and wouldn't hold the changes.

After setting [ifupdown] managed=true in /etc/NetworkManager/nm-system-settings.conf, everything seems to work now. I'm not thrilled with the hack of a workaround this method is, though. I hope it gets repaired (or regressed) before Intrepid final.

---

### Post by Coleop on 2008-10-07
The way I worked around this was to change [ifupdown] manage=false to true in the interfaces file. I then created a new connection "eth1" within networkmanager copying the MAC address from the ifupdown (eth1) entry or which ever one you are using for the new connection. I was able to make it a static connection and it was also editable. My issue now is that when I boot it defaults to the ifupdown (eth1) connection where I can't edit it to add the DNS server. I can now click the nm icon and select "eth1" and my new connection works with everything. I have tried to delete the ifupdown (eth1) entry in nm and get Removing connection failed: ifupdown - connection delete not supported (read-only).. Hope this helps some of you until a fix.

---

