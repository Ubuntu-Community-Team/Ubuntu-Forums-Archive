---
title: "Frostwire... firewall...."
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by Gael05 on 2007-07-01
Hi...
I just install frostwire on my linux ubuntu....
It does not connect to the network, because, it say it found a firewall....
I have firestarter as firewall... If I turn it off, it does not change anything....
Can someone help me...

---

### Post by janbockaert on 2007-07-01
did you tried gtk-gnutella? does it have the same problems?

---

### Post by Gael05 on 2007-07-01
Yes... it has the same problem....

---

### Post by Pumalite on 2007-07-01
If you have a router, you have to open appropiate ports. What kind of connection do you have?

---

### Post by Gael05 on 2007-07-01
What do you want to know exactly?

---

### Post by cbiere on 2007-07-01
A firewall will usually not prevent that you can connect to Gnutella. It will only prevent that others can connect to you. The same applies to your router. If you can browse the web and send mail, your router should not be the cause either. At least I doubt that any home router is by default configured to allow connections to certain ports only.

Have you tried connecting to any specific Gnutella peer?

---

### Post by Pumalite on 2007-07-01
If a router provided by company that provides the connection: no problem. But a wireless or any other kind of router has to be setup properly. A router is after all a hardware firewall. In those cases you have to open ports.

---

### Post by cbiere on 2007-07-01
When you write "open ports" do you mean allowing incoming connections on these ports or adding a port forwarding for these ports?

If so, no, you don't need to do this for Gnutella. Gnutella works mainly just like your browse except that it uses different and mostly arbitrary ports. All basic functions of Gnutella work without "opening" any ports. It is of course possible that a router or firewall is configured with utmost paranoid settings, so that you can connect only to certain ports (outgoing), for example, only 21, 25, 53, 80, 443. This is not very useful for a home user because it cripples your internet connection without adding any security.

For best performance, yes, you want to "open" a port and if you use a router configure it to forward packets for this port, so that your peer can receive incoming connections but it is not required in order to use Gnutella.

Whether you use wireless or wired access is irrelevant. Some ISPs block Gnutella and other P2P protocols.

---

### Post by Pumalite on 2007-07-01
I stand corrected. I was thinking of Azureus and Ktorrent.

---

