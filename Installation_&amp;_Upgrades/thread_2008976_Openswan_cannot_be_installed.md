---
title: "Openswan cannot be installed"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by Rayke on 2012-06-23
Hi all. I am searching for the solution to a problem whose answer has eluded me...when I attempt to download the IPSec VPN  utility, Openswan, the install fails. Here is the text i receive.

vpnaccess@ubuntu:~$ sudo apt-get install openswan
[sudo] password for vpnaccess: 
Sorry, try again.
[sudo] password for vpnaccess: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openswan-modules-source openswan-modules-dkms openswan-doc curl
The following NEW packages will be installed:
  openswan
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,073 kB of archives.
After this operation, 2,623 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  openswan
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe openswan i386 1:2.6.37-1
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openswan/openswan_2.6.37-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openswan/openswan_2.6.37-1_i386.deb)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I am a new user so I am not entirely aware of what all this means, would appreciate help on this topic though.

---

