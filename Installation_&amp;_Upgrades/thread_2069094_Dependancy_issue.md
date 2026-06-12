---
title: "Dependancy issue"
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by gopukrishnantec on 2012-10-10
Hi,

I was trying to install Dell OMSA in my ubuntu 12.04. I got the below errors while installing. Please help.


The following packages have unmet dependencies:
 srvadmin-base : Depends: srvadmin-deng (>= 7.1.0) but it is not going to be installed
                 Depends: srvadmin-hapi (>= 7.1.0) but it is not going to be installed
 srvadmin-isvc : Depends: srvadmin-deng but it is not going to be installed
                 Depends: srvadmin-hapi (>= 7.1.0) but it is not going to be installed
 srvadmin-omacore : Depends: srvadmin-deng but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Regards,

---

### Post by gopukrishnantec on 2012-10-10
While using the following command, I can see the below :
locate libpam.so.0

/lib/x86_64-linux-gnu/libpam.so.0
/lib/x86_64-linux-gnu/libpam.so.0.83.0

---

