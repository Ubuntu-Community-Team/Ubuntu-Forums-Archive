---
title: "dpkg: error : cannot read info directory"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by aithox on 2012-06-24
i accidentally deleted /var/lib/dpkg but i've restored the "status" from /var/backups/ and now i have this errors .
```
aithox@ubuntu-linux:~$ sudo apt-get install php5
[sudo] password for aithox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common
  libapache2-mod-php5 libapr1 libaprutil1 libaprutil1-dbd-sqlite3
  libaprutil1-ldap php5-cli php5-common
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom php-pear php5-suhosin
The following NEW packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common
  libapache2-mod-php5 libapr1 libaprutil1 libaprutil1-dbd-sqlite3
  libaprutil1-ldap php5 php5-cli php5-common
0 upgraded, 12 newly installed, 0 to remove and 778 not upgraded.
Need to get 0 B/8,174 kB of archives.
After this operation, 22.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: cannot read info directory: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
aithox@ubuntu-linux:~$
```

---

### Post by aithox on 2012-06-26
sudo mkdir /var/lib/dpkg/info
sudo apt-get update

:lolflag:

---

