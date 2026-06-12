---
title: "Solve this Error"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by nikhilpandey on 2013-01-12
I am having a error on ubuntu when upgrading or installing any package.
One of the error is:

[INDENT][INDENT]> nikhil@ubuntu:~$ sudo apt-get install hydra-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firebird2.5-common firebird2.5-common-doc hydra libapr1 libaprutil1 libdb4.8
  libfbclient2 libmysqlclient18 libncp libpq5 libsvn1 mysql-common
The following NEW packages will be installed
  firebird2.5-common firebird2.5-common-doc hydra hydra-gtk libapr1
  libaprutil1 libdb4.8 libfbclient2 libmysqlclient18 libncp libpq5 libsvn1
  mysql-common
0 upgraded, 13 newly installed, 0 to remove and 495 not upgraded.
1 not fully installed or removed.
Need to get 3,091 kB/3,968 kB of archives.
After this operation, 12.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise/universe firebird2.5-common-doc all 2.5.1.26351.ds4-2build1
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise/universe firebird2.5-common i386 2.5.1.26351.ds4-2build1
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise/universe libfbclient2 i386 2.5.1.26351.ds4-2build1
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise/main libsvn1 i386 1.6.17dfsg-3ubuntu3
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-updates/main libpq5 i386 9.1.7-0ubuntu12.04
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise/universe libncp i386 2.2.6-8
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise/universe hydra i386 7.1-1build1
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise/universe hydra-gtk i386 7.1-1build1
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-security/main mysql-common all 5.5.28-0ubuntu0.12.04.3
  403  Forbidden
Err [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-security/main libmysqlclient18 i386 5.5.28-0ubuntu0.12.04.3
  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/universe/f/firebird2.5/firebird2.5-common-doc_2.5.1.26351.ds4-2build1_all.deb](http://np.archive.ubuntu.com/ubuntu/pool/universe/f/firebird2.5/firebird2.5-common-doc_2.5.1.26351.ds4-2build1_all.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/universe/f/firebird2.5/firebird2.5-common_2.5.1.26351.ds4-2build1_i386.deb](http://np.archive.ubuntu.com/ubuntu/pool/universe/f/firebird2.5/firebird2.5-common_2.5.1.26351.ds4-2build1_i386.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/universe/f/firebird2.5/libfbclient2_2.5.1.26351.ds4-2build1_i386.deb](http://np.archive.ubuntu.com/ubuntu/pool/universe/f/firebird2.5/libfbclient2_2.5.1.26351.ds4-2build1_i386.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-common_5.5.28-0ubuntu0.12.04.3_all.deb](http://np.archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-common_5.5.28-0ubuntu0.12.04.3_all.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/libmysqlclient18_5.5.28-0ubuntu0.12.04.3_i386.deb](http://np.archive.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/libmysqlclient18_5.5.28-0ubuntu0.12.04.3_i386.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.6.17dfsg-3ubuntu3_i386.deb](http://np.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.6.17dfsg-3ubuntu3_i386.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/libpq5_9.1.7-0ubuntu12.04_i386.deb](http://np.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/libpq5_9.1.7-0ubuntu12.04_i386.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/universe/n/ncpfs/libncp_2.2.6-8_i386.deb](http://np.archive.ubuntu.com/ubuntu/pool/universe/n/ncpfs/libncp_2.2.6-8_i386.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/universe/h/hydra/hydra_7.1-1build1_i386.deb](http://np.archive.ubuntu.com/ubuntu/pool/universe/h/hydra/hydra_7.1-1build1_i386.deb)  403  Forbidden
Failed to fetch [http://np.archive.ubuntu.com/ubuntu/pool/universe/h/hydra/hydra-gtk_7.1-1build1_i386.deb](http://np.archive.ubuntu.com/ubuntu/pool/universe/h/hydra/hydra-gtk_7.1-1build1_i386.deb)  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/INDENT][/INDENT]
[INDENT][/INDENT]

---

### Post by 2F4U on 2013-01-12
Could be a problem with the mirror you are currently using. Have you tried selecting a different mirror?

---

### Post by Cheesehead on 2013-01-13
+1

2F4U is right. Bad mirror.

---

