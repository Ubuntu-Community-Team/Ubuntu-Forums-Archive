---
title: "Installing packages Ubuntu 7.04 Server"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by caspert_ghost on 2007-05-23
I am very very new to ubuntu, linix, networking yada yada yada... I have been running my test server and scripts from a windows box for the past 7 years. I really wanted to create my own nix box but it looks like I may have to revert back to windows.

I have been able to install some packages in fact most, but now I am on step 15 of the perfect setup and cannot install apache/php5
My problem is every time I apt-get install a package I get this error.

```
root@webserver:~# apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils libexpat1 ssl-cert
Reading package lists... Done
Building dependency tree
Reading state information... Done
apache2-doc is already the newest version.
libexpat1 is already the newest version.
ssl-cert is already the newest version.
The following extra packages will be installed:
  apache2.2-common libaprutil1 libpq5
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common libaprutil1
  libpq5
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 223kB/2030kB of archives.
After unpacking 5829kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com feisty-security/main libpq5 8.2.4-0ubuntu0.7.04
  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.2/libpq5_8.2.4-0ubuntu0.7.04_i386.deb  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

So I run apt-get update
```
root@webserver:~# apt-get update
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 3B in 30s (0B/s)
Reading package lists... Done
```

Then run it again
```
root@webserver:~# apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils libexpat1 ssl-cert --fix-missing
Reading package lists... Done
Building dependency tree
Reading state information... Done
apache2-doc is already the newest version.
libexpat1 is already the newest version.
ssl-cert is already the newest version.
The following extra packages will be installed:
  apache2.2-common libaprutil1 libpq5
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common libaprutil1
  libpq5
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 223kB/2030kB of archives.
After unpacking 5829kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com feisty-security/main libpq5 8.2.4-0ubuntu0.7.04
  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.2/libpq5_8.2.4-0ubuntu0.7.04_i386.deb  Connection failed
root@webserver:~#
```
Anyone know how to solve this or shall I leave linux with a bad taste and go back to windows?

---

### Post by caspert_ghost on 2007-05-24
anyone have any ideas what the problem is?

---

### Post by maeve_zahra on 2007-05-24
i got the same error too, i try to apt-install update but it always failed for universe repository. any idea what's going on guys?

---

### Post by ahardo on 2008-06-25
yup i got the same errors too, i m using ubuntu 7.10 server... but until now, i always got this error.. what should i do to this error ? can anyone help me ?

---

