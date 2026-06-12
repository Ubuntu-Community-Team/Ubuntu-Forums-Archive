---
title: "can't ping DNS server"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by wmburke on 2005-05-31
I have Hoary 5.04 installed as a dual boot on my laptop. Everything works fine on w2k side.

I'm trying to connect wirelessly to the internet through a well-established wireless network, so I know the router and there on out is properly set up.

I can connect and get proper dhcp setup, however, I can only ping the gateway, myself, and other machines on the network. I can't even ping the DNS server, and certainly any sort of internet is out of the question.

Route shows:

```

Destination   Gateway       Genmask       Flags Metric Ref Use Iface
192.168.0.0   *             255.255.255.0 U     0       0   0  eth1
default       192.168.0.1   0.0.0.0       UG    0       0   0  eth1

```

I'm at a loss for how to fix this.

Please advise me.

Wayne

---

### Post by wmburke on 2005-06-10
For completeness:

I tried everything I could think of, and got some help from other forums to verify that my ubuntu was set up correctly. Everything seemed fine.

At one point, I set up the wired access and it worked fine.

The next day when I booted into Ubuntu, the wireless worked and continues to today.

I don't know what sense this makes, but there you go...

---

### Post by Joeb on 2005-06-10
[QUOTE=wmburke]For completeness:

I tried everything I could think of, and got some help from other forums to verify that my ubuntu was set up correctly. Everything seemed fine.

At one point, I set up the wired access and it worked fine.

The next day when I booted into Ubuntu, the wireless worked and continues to today.

I don't know what sense this makes, but there you go...[/QUOTE]


Is your dns server on your sub-net or is it at your ISP's?  I can't ping my DNS server either (the ISP one), however, my router accepts dns requests and forwards them on or I can hard code the ISP dns servers in the network settings.

So, it might be normal that you can't ping the DNS server.  Is that your only problem or is it also that you can't access web pages?

---

