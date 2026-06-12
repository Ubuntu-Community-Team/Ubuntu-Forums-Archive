---
title: "Unable to fetch some archives"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by MikeM™ on 2008-09-04
hi guys,

greetings!

i am using ubuntu server (Linux int-vms5 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2008 x86_64 GNU/Linux) and what i am trying to do is to "sudo apt-get install -y ia32-libs" for my vmware server 1.0.6.  i tried changing my /etc/apt/sources.list from ph.archive.ubuntu.com to archive.ubuntu.com and still the same error.  here it is:

===
super@int-vms5:/opt/downloads/vmware-server-distrib$ sudo apt-get install -y ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  java-common
Use 'apt-get autoremove' to remove them.
Recommended packages:
  lib32nss-mdns
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 20.9MB of archives.
After this operation, 101MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe ia32-libs 2.2ubuntu11 [20.9MB]
Fetched 20.9MB in 1min20s (260kB/s)                                            
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu11_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu11_amd64.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
===

could you please shed some light on this?  did i miss any on the installation?  thanks much in advance!


kudos!

---

