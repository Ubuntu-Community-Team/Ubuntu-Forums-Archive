---
title: "install with static IP address"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by bkline on 2007-06-13
How do I tell the installation of Ubuntu 7.04 (i386) that I'm not using a DHCP server (the machine's got its own address)?

Thanks,
Bob

---

### Post by merlinus on 2007-06-13
IIRC, a screen will come up in terms of detecting and setting up your card, and you can specify at that point the static IP address.

If not, you can change this when ubuntu is up-and-running.

-merlin

---

### Post by bkline on 2007-06-13
> **merlinus said:**
> IIRC, a screen will come up in terms of detecting and setting up your card, and you can specify at that point the static IP address.

If not, you can change this when ubuntu is up-and-running.

-merlin

I guess they've eliminated the screen that asks about an IP address when the network card is detected, and when I went in to the Network administrative tool and plugged in the static IP address, netmask, gateway, and DNS server, I found I was still offline because it hadn't set the route.  Strange, never had this problem with Ubuntu before.  I guess they're thinking "Ubuntu's for ordinary users, and ordinary users don't have static IP addresses."

Cheers,
Bob

---

### Post by merlinus on 2007-06-13
Yeah, now I remember.  When I installed on my 5-year-old Compaq notebook, the card was not detected automatically.  That's when the manual configuration choice appeared.

Glad it's working....

-merlin

---

