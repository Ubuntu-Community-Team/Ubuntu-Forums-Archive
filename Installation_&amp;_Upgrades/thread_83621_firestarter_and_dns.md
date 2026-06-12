---
title: "firestarter and dns"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by domkle on 2005-10-29
My problem is strange
Upgraded my desktop machine and internet frontend machine from a working Fedora 3 to AM64 Ubuntu 5.10

Everything is nice and dandy, up to Firestarter.
Used successfully Firestarter to share internet under Fedora using same hardware.

Under Ubuntu it does not work.

The symptoms are:
1) if I activate the firewall even on the desktop I don't have the DNS working anymore. I stop FS and it works again????
2) Firestarter complains each time I start it that it can't start the DHCP server, but starting it by hand through /etc/init.d/dhcp3... start works well.

Any help appreciated,
have  days in front of me, if I can't get it to work will have to switch back to fedora ;))

Thanks

---

### Post by domkle on 2005-11-02
OK silly me,
It works now, had to read carefully other posts on the same subject.

I had to
1) install bind9 that is not installed by default.
2) push the dhcp.conf file from /etc to /etc/dhcp3

And now everything works nicely
Nice day to you

---

### Post by kakashi on 2005-11-02
why don;t you use guidedog to configure iptables for you so you can share internet.
it really is a far supereior solution.
theres also a firewall with a simialar name. guarddog maybe

---

