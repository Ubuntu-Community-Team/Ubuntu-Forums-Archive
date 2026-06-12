---
title: "problem with resolvconf service"
date: 2022-08-28
forum: Installation &amp; Upgrades
---

### Post by vormsty on 2022-08-28
Hello,
I installed dnsmasq.
I understand dns server must be written on /etc/resol.conf file.
I understand resolv.conf is overwritten at startup.
I understand I have to install resolvconf package.
I understand dns server must be written in /etc/resolvconf/resolv.conf.d/head
ok
but...
At startup dnsmasq log says ther is no nameserver in the file /run/dnsmasq/resolv.conf

How can I solve this issue ?



Many thanks for your help.
Best regards

Thierry

---

### Post by ActionParsnip on 2022-08-28
What is the output of
```

lsb_release -a; uname -a; dpkg -l | grep -i dns

```
Thanks

---

### Post by vormsty on 2022-08-29
Hello, the result:
lsb_release -a; uname -a; dpkg -l | grep -i dns
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy
Linux Nuc 5.15.0-46-generic #49-Ubuntu SMP Thu Aug 4 18:03:25 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
ii  avahi-daemon                               0.8-5ubuntu5                            amd64        Avahi mDNS/DNS-SD daemon
ii  bind9-dnsutils                             1:9.18.1-1ubuntu1.1                     amd64        Clients provided with BIND 9
ii  bind9-host                                 1:9.18.1-1ubuntu1.1                     amd64        DNS Lookup Utility
ii  dns-root-data                              2021011101                              all          DNS root data including root zone and DNSSEC key
ii  dnsmasq                                    2.86-1.1ubuntu0.1                       all          Small caching DNS proxy and DHCP/TFTP server
ii  dnsmasq-base                               2.86-1.1ubuntu0.1                       amd64        Small caching DNS proxy and DHCP/TFTP server
ii  dnsutils                                   1:9.18.1-1ubuntu1.1                     all          Transitional package for bind9-dnsutils
ii  ldnsutils                                  1.7.1-2ubuntu4                          amd64        ldns library for DNS programming
ii  libavahi-core7:amd64                       0.8-5ubuntu5                            amd64        Avahi's embeddable mDNS/DNS-SD library
ii  libdns-export1110                          1:9.11.19+dfsg-2.1ubuntu3               amd64        Exported DNS Shared Library
ii  libldns3:amd64                             1.7.1-2ubuntu4                          amd64        ldns library for DNS programming
ii  libnss-mdns:amd64                          0.15.1-1ubuntu1                         amd64        NSS module for Multicast DNS name resolution

Many thanks for your help !

---

### Post by TheFu on 2022-08-29
> **vormsty said:**
> Hello,
I installed dnsmasq.

Fine. why?

> **vormsty said:**
> I understand dns server must be written on /etc/resol.conf file.

That's the wrong filename.  Details matter. Being correct when posting matters too, so we don't waste time with stuff like this.

> **vormsty said:**
> 
I understand resolv.conf is overwritten at startup.

Sometimes, but not always.

> **vormsty said:**
> 
I understand I have to install resolvconf package.

No. This is wrong.  You don't need resolvconf.  Most recent Ubuntu's have switched to systemd-resolved to manage the /etc/resolv.conf file.  You don't need that either.  If you have to choose, go with systemd-resolved, not resolvconf.  Basically, I'm saying that you made a mistake installing resolvconf and should remove --purge it and all files related to it.

> **vormsty said:**
> 
I understand dns server must be written in /etc/resolvconf/resolv.conf.d/head
ok
but...
At startup dnsmasq log says ther is no nameserver in the file /run/dnsmasq/resolv.conf

How can I solve this issue ?


Why are you using dnsmasq?  What's the purpose?  Then we can make suggestions for the best solution which may not include dnsmasq at all.
Of course, "because I wanted an internal DNS server" is a fine answer too, assuming there are a few other devices on the LAN that would require a local DNS, but for fewer than 5 computers, keeping the /etc/hosts on each maintained is much easier.

---

### Post by &amp;KyT$0P# on 2022-08-29
> **TheFu said:**
> No. This is wrong.  You don't need resolvconf.  Most recent Ubuntu's have switched to systemd-resolved to manage the /etc/resolv.conf file.  You don't need that either.  If you have to choose, go with systemd-resolved, not resolvconf.  Basically, I'm saying that you made a mistake installing resolvconf and should remove --purge it and all files related to it.

Not necessarily.  This, too, depends on what purpose(s) they're trying to use dnsmasq for.

---

