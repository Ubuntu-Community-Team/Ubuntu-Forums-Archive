---
title: "Preseed help with custom install"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by TeMpEsT_BR on 2007-12-07
Hi!

I'm trying to learn how to make custom installs of ubuntu on my network. I'm making a preseed file that's going to be downloaded when the installation process start.

I already made many installations using Kickstart for fedora and RHEL. Now i'm trying to build something similar for ubuntu using preseed for D-I.


My real question is: Is it possible to make a full unattended installation process using preseed, passing it as a parameter for the alternative ubuntu 7.10 CD?

I need to configure the Network adresses and the NIS domain using the preseed file.

I'm using this to configure the network, but it's not working.. It keeps using DHCP...
# Static network configuration.
d-i netcfg/get_nameservers string 10.10.10.10
d-i netcfg/get_ipaddress string 10.10.10.10
d-i netcfg/get_netmask string 255.255.2255.0
d-i netcfg/get_gateway string 10.10.10.10
d-i netcfg/confirm_static boolean true

And to configure the NIS:
d-i nis/domain string my.domain

I'm passing NIS package in the package selection, but it's not configuring the correct domain


Can anyone help me?

Thanks!

---

