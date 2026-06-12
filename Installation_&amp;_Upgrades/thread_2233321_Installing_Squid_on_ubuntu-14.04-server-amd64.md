---
title: "Installing Squid on ubuntu-14.04-server-amd64"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by Raoken on 2014-07-07
I have completed a brand new install from this iso on a VMware esxi vm.

Logged in as root. Changed IP to from DHCP to static by editing /etc/network/interfaces. Tested and can now ssh in via that IP.

After much searching and testing "reported" methods to install squid on Ubuntu I have not been successful. Either the guides are outdated, I have missed a pre-install step, or I am just not getting something. I am not an idiot, and know lots of flavours of *nix. It has been however a long time since I've used Linux.

The command steps I was using as follows :

1. apt-get update
2. apt-get install squid

Now the update completes fine. The results of the apt-get for the squid package seems different for all the other guides. (Not to mention a lot of the guides include a third argument like "squid-common". Here is some output as a result.

[I]# apt-get install squid
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  squid
0 to upgrade, 1 to newly install, 0 to remove and 41 not to upgrade.
Need to get 0 B/5,964 B of archives.
After this operation, 141 kB of additional disk space will be used.
Selecting previously unselected package squid.
(Reading database ... 87449 files and directories currently installed.)
Preparing to unpack .../squid_3.3.8-1ubuntu6_amd64.deb ...
Unpacking squid (3.3.8-1ubuntu6) ...
Setting up squid (3.3.8-1ubuntu6) ...[/I]

After this there is no /etc/squid folder.

Can anyone please explain what im missing here?

---

### Post by Raoken on 2014-07-09
No one here was able to help so I switched to Centos and had it up and running in a few hours, using basically the same method, just yum instead of apt-get.

---

### Post by SeijiSensei on 2014-07-10
Ubuntu, and probably Debian, often append a version number to directories like /etc/squid and /etc/apache.  So your Squid configuration was in /etc/squid3; Apache configurations are in /etc/apache2.  I suppose this method is designed to enable multiple versions to run on a single machine, but it is confusing to those of us who started off in the RedHat world where directories are named things like /etc/squid.

---

