---
title: "Configuring 7.04 Server with Roadrunner cable modem"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by gbutler288 on 2007-05-14
I'm trying to setup my 7.04 Ubuntu Server on my RoadRunner Cable Modem.  I've used the following configuration:

/etc/network/interfaces

auto eth0
iface eth0 inet dhcp

In XP if I do a ipconfig /all it says dhcp is enabled
IP Address is:  24.93.124.144
Subnet Mask: 255.255.252.0
Gateway:  24.93.124.1
DHCP Server:  10.36.32.1
DNS Server:  65.24.7.3


It doesn't seem to be working.  I shouldn't need DHCP but I'm not sure how to get around this.  I'm trying to do the apt-get update and run some stuff but I cannot get connected to the internet to get even that far.  I'm really getting frustrated any help would be appreciated.  I've searched google for a couple of days.  I'm sure its probably something simple.

Thanks in advance,

Gary

---

### Post by dfreer on 2007-05-14
try doing this:
```
sudo dhclient eth0
```

---

### Post by gbutler288 on 2007-05-14
I tried that and I get No working leases in persisten database - sleeping?

---

### Post by kenny1948 on 2007-08-01
I was having a similar problem.  I unintalled my cable modem, and then re-intalled it.  When I did everything worked fine.

---

