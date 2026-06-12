---
title: "dpkg"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by bl00dang3l on 2010-06-03
Hello, I was trying to install proftd and I got this error. Any help would be appreciated. Thank you.
```
tpsv@titantest:~$ sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting proftpd-basic instead of proftpd
The following extra packages will be installed:
  libssl-dev libssl0.9.8 openbsd-inetd proftpd-basic
Suggested packages:
  proftpd-doc openssl proftpd-mod-mysql proftpd-mod-pgsql proftpd-mod-ldap
  proftpd-mod-odbc proftpd-mod-sqlite
The following NEW packages will be installed:
  openbsd-inetd proftpd-basic
The following packages will be upgraded:
  libssl-dev libssl0.9.8
2 upgraded, 2 newly installed, 0 to remove and 1231 not upgraded.
Need to get 5,908kB of archives.
After this operation, 2,658kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com lucid/main libssl-dev 0.9.8k-7ubuntu8 [2,001kB]
Get:2 http://us.archive.ubuntu.com lucid/main libssl0.9.8 0.9.8k-7ubuntu8 [3,003kB]
Get:3 http://us.archive.ubuntu.com lucid/main openbsd-inetd 0.20080125-4ubuntu2 [37.0kB]
Get:4 http://us.archive.ubuntu.com lucid/universe proftpd-basic 1.3.2c-1 [866kB]
Fetched 5,908kB in 2min 29s (39.5kB/s)                                         
Preconfiguring packages ...
Selecting previously deselected package libssl-dev.
(Reading database ... 70%dpkg: unrecoverable fatal error, aborting:
 files list file for package `grub-pc' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
tpsv@titantest:~$ 

```

---

### Post by dino99 on 2010-06-03
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

into synaptic: choose downloading from "main server", then update

sudo apt-get install -f
sudo dpkg --configure -a

then reinstall your package proftpd

---

### Post by bl00dang3l on 2010-06-03
Well it didn't fix it, but its now a different result.
```
tpsv@titantest:~$ sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting proftpd-basic instead of proftpd
The following extra packages will be installed:
  openbsd-inetd proftpd-basic
Suggested packages:
  proftpd-doc openssl proftpd-mod-mysql proftpd-mod-pgsql proftpd-mod-ldap
  proftpd-mod-odbc proftpd-mod-sqlite
The following NEW packages will be installed:
  openbsd-inetd proftpd-basic
0 upgraded, 2 newly installed, 0 to remove and 54 not upgraded.
Need to get 836kB of archives.
After this operation, 2,195kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com karmic/main openbsd-inetd 0.20080125-2ubuntu1 [37.2kB]
Get:2 http://archive.ubuntu.com karmic/universe proftpd-basic 1.3.2-3 [799kB]
Fetched 836kB in 13s (60.3kB/s)                                                
Preconfiguring packages ...
debconf: DbDriver "templatedb": could not sync /var/cache/debconf/templates.dat-new: Input/output error
Selecting previously deselected package openbsd-inetd.
(Reading database ... 70%dpkg: unrecoverable fatal error, aborting:
 files list file for package `grub-pc' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by bl00dang3l on 2010-06-07
Help?

---

