---
title: "Dapper only works on recovery mode"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by emamm on 2006-07-17
Hello

Since the installation process won't give me much choice regarding networking  as far as I know (it got a dhcp lease from the router), I blindly changed the hostname and ip address.  The modified files were:

more /etc/hosts
127.0.0.1       localhost
192.168.0.2     ut-eacghome -> it used to be 127.0.0.1 armagedon

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

more /etc/hostname 
ut-eaghome armagedon -< it used to be armagedon

When the system boots in normal mode, it gets stuck just after HP ..Imaging software.  No warning messages, nothing.  

Any ideas on how to get the system going with the modification above.

Many thanks

Ed


PS. On recovery mode,  X starts for root.

---

