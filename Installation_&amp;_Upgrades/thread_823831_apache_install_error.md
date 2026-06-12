---
title: "apache install error"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by madmax797 on 2008-06-09
not sure if my previous post worked.. posting again

iam getting error installing apache.. appreciate any help

sudo apt-get install apache2 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libpq5
Suggested packages:
  apache2-doc
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common libapr1
  libaprutil1 libpq5
0 upgraded, 7 newly installed, 0 to remove and 3 not upgraded.
Need to get 1614kB of archives.
After this operation, 5755kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libapr1 libpq5 libaprutil1 apache2-utils apache2.2-common apache2-mpm-worker
  apache2
Install these packages without verification [y/N]? y
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libapr1 1.2.11-1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libpq5 8.3.1-1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libaprutil1 1.2.12+dfsg-3
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main apache2-utils 2.2.8-1ubuntu0.1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main apache2.2-common 2.2.8-1ubuntu0.1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main apache2-mpm-worker 2.2.8-1ubuntu0.1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main apache2 2.2.8-1ubuntu0.1
  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.11-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.11-1_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.1-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.1-1_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.2.12+dfsg-3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.2.12+dfsg-3_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.8-1ubuntu0.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.8-1ubuntu0.1_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.8-1ubuntu0.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.8-1ubuntu0.1_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-worker_2.2.8-1ubuntu0.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-worker_2.2.8-1ubuntu0.1_i386.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.1_all.deb) 404 Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

running apt-get update also gives me HTTP 404 error

---

### Post by madmax797 on 2008-07-08
i ran this as my user, with sudo and it didnt work.. so i did su - root and then ran same command.. that worked fine.. not sure why the sudo thing doesn't work.. oh well.. now to getting it configured.

---

### Post by HDave on 2009-08-14
Just got this myself.  It means you have to do an "aptitude update" first.

---

