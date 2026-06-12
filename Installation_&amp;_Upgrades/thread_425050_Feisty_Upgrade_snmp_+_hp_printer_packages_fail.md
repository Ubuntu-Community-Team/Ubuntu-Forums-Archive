---
title: "Feisty Upgrade: snmp + hp printer packages fail"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by flickerfly on 2007-04-27
When I run sudo apt-get upgrade, it tells me that these packages aren't configured:
 libsnmp-base
 libsnmp9
 hplip
 hpijs
 foomatic-db-hpijs
 ubuntu-desktop

The HP stuff depend on snmp stuff which all works it's way back to this package: libsnmp-base. 

When I try to configure that package and get things moving, this is my error.

$ sudo dpkg --configure libsnmp-base
```
Setting up libsnmp-base (5.2.3-4ubuntu1) ...
dpkg: error processing libsnmp-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libsnmp-base

```

I tried these commands to clean things up just in case:
$ sudo dpkg --purge libsnmp-base libsnmp9 hplip hpijs foomatic-db-hpijs
$ sudo rm /var/cache/apt/archives/<packages affected by this>

This command tells me that the packages I need aren't authenticated.

$ sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  foomatic-db-hpijs hpijs libsnmp-base libsnmp9
Suggested packages:
  hplip hpoj hpijs-ppds hplip-doc
The following NEW packages will be installed:
  foomatic-db-hpijs hpijs libsnmp-base libsnmp9
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 3657kB of archives.
After unpacking 12.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libsnmp-base libsnmp9 hpijs foomatic-db-hpijs
Install these packages without verification [y/N]? 
E: Some packages could not be authenticated
```

So what do I need to do next?  :confused:

Edit: I resolved the authentication problem with an apt-get update and downloaded fresh copies of the packages, but am still not able to get them installed.

---

