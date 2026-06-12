---
title: "minimal Ubuntu installation without X, with just DHCP support"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by cccc on 2013-06-09
Hi

Is it possible to do absolute minimal Ubuntu installation without X, with just DHCP support?
BTW Which Ubuntu packages do I need exactly for DHCP support?

---

### Post by steeldriver on 2013-06-09
DHCP *client* support is a standard part of the Ubuntu Server edition - at least on 12.04. Or do you need a DHCP server? the package for that would be *isc-dhcp-server* I think

---

### Post by Cheesemill on 2013-06-09
Yes it is. A minimal installation doesn't have X installed.

If you mean DHCP client support then this is already included in the packages that are installed with a minimal installation.

If you need a DHCP server then this can be achieved by installing either the dnsmasq or isc-dhcp-server packages.

To install a minimal system you have two options, you can either use the [mini CD]("http://cdimage.ubuntu.com/netboot/") which downloads all needed packages from the internet so you start with a fully updated system, or you can use the server CD and hit F4 to select 'Install a minimal system'. If you are after the smallest installation possible then use the server CD, I'm not exactly sure which packages are left out but you end up with around 50 fewer packages installed than if you use the mini CD, you can see the testing I did [here]("http://ubuntuforums.org/showthread.php?t=2037561&p=12156448&viewfull=1#post12156448").

---

