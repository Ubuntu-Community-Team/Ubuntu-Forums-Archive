---
title: "PXE Kernel Boot Parameters and LDAP/NIS Connection"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by vinterkind on 2011-09-21
Hi all,

I've trying to install Ubuntu 10.04 LTS Desktop via NFS and PXE.

My PXE Environment ist just fine, I can install Scientific Linux without any problems.
If you'd like more info about the configuration - just ask.

So here we go. 
Installation via "netboot"-folder is okay but not really the way I'd like to use it.
The real "network" installation over the Internet works!

[B]2 Questions
1. Is there any possible way to boot the cd's default kernel (_not casper_) with nfs/ip ?[/B]

I've tried the following (excerpt from pxelinux.cfg)
```
menu label ^Ubuntu 10.04 LTS Desktop
  menu default
  kernel /ubu/install/vmlinuz
  append root=/dev/nfs nfsroot=<nfsserver>:/nfsroot/ubu ip=dhcp initrd=/ubu/install/initrd.gz
```It starts until the Installation wants to check for the CDRom.
And I've got no possibility to mount the NFS Share from my console.

**2. Is there any way to connect Ubuntu to LDAP or NIS while Installing ?**
I really don't want to create a local user. 
Up until now, I need to install ubuntu complete to install the nis-tools / configure it and delete the local user.

Any help is appreciated!
Cheers, ):P

---

