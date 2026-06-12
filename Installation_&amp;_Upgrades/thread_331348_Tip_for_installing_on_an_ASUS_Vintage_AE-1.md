---
title: "Tip for installing on an ASUS Vintage AE-1"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by dhuff on 2007-01-04
I just went through a certain amt of pain getting Ubuntu 6.06 LTS up and running on my new [ASUS Vintage AE-1]("http://www.asus.com/products4.aspx?modelmenu=1&model=568&l1=1&l2=1&l3=0") barebones system and thought I'd share how I solved the installation problems.

The main issue is the, errr..."problematic" SiS190 ethernet chipset on the motherboard. It requires an MTU size of 1492 to work under Linux, not the default 1500. So you'll want to start up the alternate, text-based install of Ubuntu and, when it asks if you want to configure the network hardware, just choose not to do so during the install. 

Once the system is up, *then* configure the network hardware, and add an MTU stmt to your /etc/network/interfaces file thusly:

```
iface eth0 inet dhcp
mtu 1492
```

---

### Post by dhuff on 2007-04-26
Just tried the 7.04 "Feisty" Live CD on this system and the problem with the MTU size persists...

---

