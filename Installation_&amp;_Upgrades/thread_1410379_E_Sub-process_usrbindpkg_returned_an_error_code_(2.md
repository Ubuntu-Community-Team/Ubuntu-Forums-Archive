---
title: "E: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by jammyozzy on 2010-02-18
Hey all, just did a fresh install of XUbuntu 9.10 a couple of days ago to play around with as a file server. Just now I tried to uninstall vsftpd and got this out of the console:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-utils libaprutil1-dbd-sqlite3 apache2.2-bin libapr1 libaprutil1-ldap
  apache2.2-common apache2-mpm-worker libaprutil1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  vsftpd
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 479kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 35%dpkg: unrecoverable fatal error, aborting:
 files list file for package `vsftpd' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I've tried running 'dpkg --configure -a' and running the command in the starred post here:[ https://answers.launchpad.net/ubuntu/+question/2591]("https://answers.launchpad.net/ubuntu/+question/2591") but these have been no help. CAn somebody shed some light on what's gone wrong here?

---

### Post by jammyozzy on 2010-02-20
Anybody?

---

### Post by Wobblybob on 2011-02-15
I'm using Xubuntu Natty and just did my usual sfae upgrade with;

$ sudo aptitude update && sudo aptitude safe-upgrade

and got the same error message and tried the following;

$ sudo dpkg --clear-avail

then

$ sudo aptitude safe-upgrade
 
and it fixed the issue for me

---

