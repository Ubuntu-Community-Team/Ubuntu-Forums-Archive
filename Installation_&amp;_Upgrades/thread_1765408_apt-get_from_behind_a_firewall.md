---
title: "apt-get from behind a firewall"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by sridharpandu on 2011-05-23
i have installed Ubuntu 10.04 server and would like to install the updates after updating my package information. I have done this from a static ip connection but this time I am behind a firewall and I am using a DHCP server. I have modified my /etc/networking/interfaces file to have the following entries
auto eth0
iface eth0 inet dhcp
dns-nameservers my.dns.ip.add
 
then ran the command -> invoke-rc.d networking restart
 
I modified /etc/dhc3/dhcpclient.conf to have the following entries
prepend  my.dns.ip.add
request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, net-bios-name-servers, netbios-scope;
 
then ran the command -> invoke-rc.d networking restart
I get the bound to message.
 
DHCP is listening on port 67 (UDP port and its not blocked in the firewall)
 
I then ran -> apt-get update I get the following errors
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-Security Release.gpg
temporary failure resolving security.ubuntu.com 
some more lines of the same error for other updates
 
Has anyone faced this problem. Would appreciate any help.

---

