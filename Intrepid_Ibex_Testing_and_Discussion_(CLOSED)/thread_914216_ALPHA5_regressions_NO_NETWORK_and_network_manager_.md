---
title: "ALPHA5 regressions: NO NETWORK and network manager gateway"
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-09-08
The ethernet network works with kernel 2.6.26-5 but not with 2.6.27-2.

It's strange because I'm able to do correctly traceroute but I can't load a page with firefox or update synaptic :confused:

Another important issue is that I can't setup manually the gateway with NM, the button to apply the settings is alwais disabled. :confused:

sudo route del default
sudo route add default 192.168.1.2 is still the easiest way and fortunatly it WORKS!!

---

### Post by scaine on 2008-09-08
I've just tried it here on both DHCP and manually configured.  Both work fine.  When using manual configuration, the okay button is greyed out until a valid netmask (I used 255.255.255.0) is entered.  I could add a gateway afterwards without any probs.

If you can traceroute/ping, but can't use firefox, there might be a DNS issue.  When you use traceroute, are you using a hostname or IP address?

But since you can't actually enter a gateway with NM, I have to assume that this is an issue with your network card.  Can't really help you there - I'm a network analyst and I haven't a clue what kind of card is in my PC!  It just works and luckily always has...

If I can ask, why are you having to add a gateway?  This would normally be issued by your DHCP server on your router.

---

### Post by Nullack on 2008-09-08
There is a number of bugs in NM 0.7 that isnt fixed yet, refer to my post on that.

---

