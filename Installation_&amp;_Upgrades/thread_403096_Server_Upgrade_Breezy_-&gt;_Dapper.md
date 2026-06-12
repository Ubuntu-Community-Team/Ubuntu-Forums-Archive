---
title: "Server Upgrade Breezy -&gt; Dapper"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by iamjakex on 2007-04-06
I am trying to run the Breezy -> Dapper upgrade and am running into problems:
```

root@LFSfiles:/home/jakex # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  binutils-static libdns21 libisc11 liblwres9 libmysqlclient15off libparted1.6-13 linux-image-2.6.15-28-amd64-generic
  linux-restricted-modules-2.6.15-28-amd64-generic linux-restricted-modules-common mysql-client-5.0 mysql-server-5.0 openssl ssl-cert
  vim-runtime
The following packages will be upgraded:
  bind9-host dnsutils ftp libbind9-0 libdbd-mysql-perl libisccc0 libisccfg1 linux-image-amd64-generic
  linux-restricted-modules-amd64-generic lvm2 lynx mdadm mutt mysql-client mysql-server ntp openssh-client openssh-server parted
  postfix tcpdump vim vim-common w3m wget
25 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/72.9MB of archives.
After unpacking 168MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 15119 files and directories currently installed.)
Preparing to replace lvm2 2.01.04-5ubuntu1 (using .../lvm2_2.02.02-1ubuntu1.5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1.5_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1.5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@LFSfiles:/home/jakex #

```

I updated the apt source.list and ran apt-getupdate && apt-get dist-upgrade
But am getting errors.. some stuff seems to be upgraded (like what I wanted.. Samba)

Any thoughts?
:( :confused:

---

### Post by zvacet on 2007-04-07
Maybe this will help
```
sudo aptitude upgrade

```

---

