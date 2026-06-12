---
title: "Error when failed to install Openprinting-gutenprint ??"
date: 2017-03-31
forum: Installation &amp; Upgrades
---

### Post by Janemba_Bananamba on 2017-03-31
I got this error HELP.

```

sudo apt-get autoremove
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0 B/2.275 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing package libc6:i386 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of liblzma5:i386:
 liblzma5:i386 depends on libc6 (>= 2.4); however:
  Package libc6:i386 is not configured yet.


dpkg: error processing package liblzma5:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpcre3:i386:
 libpcre3:i386 depends on libc6 (>= 2.4); however:
  Package libc6:i386 is not configured yet.


dpkg: error processing package libpcre3:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgpg-error0:i386:
 libgpg-error0:i386 depends on libc6 (>= 2.15); however:
  Package libc6:i386 is not configured yet.


dpkg: error processing package libgpg-error0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgcrypt20:i386:
 libgcrypt20:i386 depends on libc6 (>= 2.15); however:
  Package libc6:i386 is not configured yet.
 libgcrypt20:i386 depNo apport report written because the error message indicates its a followup error from a previous failure.
                                               No apport report written because the error message indicates its a followup error from a previous failure.
                                                                         No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         ends on libgpg-error0 (>= 1.14); however:
  Package libgpg-error0:i386 is not configured yet.


dpkg: error processing package libgcrypt20:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libselinux1:i386:
 libselinux1:i386 depends on libc6 (>= 2.8); however:
  Package libc6:i386 is not configured yet.
 libselinux1:i386 depends on libpcre3; however:
  Package libpcre3:i386 is not configured yet.


dpkg: error processing package libselinux1:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zlib1g:i386:
 zlib1g:i386 depends on libc6 (>= 2.4); however:
  Package libc6:i386 is not configured yet.


dpkg: error processing package zlib1g:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpng12-0:i386:
 libpng12-0:i386 depends on libc6 (>= 2.11); however:
  Package libc6:i386 is not configured yet.
 libpng12-0:i386 depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g:i386 is not configured yet.


dpkg: error processing package libpng12-0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on libc6:i386 | libc6-i386; however:
  Package libc6:i386 is not configured yet.
  Package libc6-i386 is not installed.
 lsb-core depends on zlib1g:i386 | lib32z1; however:
  Package zlib1g:i386 is not configured yet.
  Package lib32z1 is not installed.


dpkg: error processing package lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-printing:
 lsb-printing depends on lsb-core (>= 9.20160110ubuntu0.2); however:
  Package lsb-core is not configured yet.


dpkg: error processing package lsb-printing (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core (>= 9.20160110ubuntu0.2); however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-printing (>= 9.20160110ubuntu0.2); however:
  Package lsb-printing is not configured yet.


dpkg: error processing package lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6:i386
 liblzma5:i386
 libpcre3:i386
 libgpg-error0:i386
 libgcrypt20:i386
 libselinux1:i386
 zlib1g:i386
 libpng12-0:i386
 lsb-core
 lsb-printing
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

guy i need help please..
i cant install other software

---

