---
title: "Cannot install mysql in ubuntu server"
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by neoncyber on 2013-07-16
Hello, I've just installed an ubuntu-server 13.04 virtual machine and I just wanted to install mysql-server and got the next problem
```

$ sudo bash
# apt-get install mysql-server

```
and got the next result
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libaio1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient18 libnet-daemon-perl
  libplrpc-perl libterm-readkey-perl mysql-client-5.5 mysql-client-core-5.5 mysql-common
  mysql-server-5.5 mysql-server-core-5.5
Suggested packages:
  libipc-sharedcache-perl tinyca mailx
The following NEW packages will be installed:
  libaio1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient18 libnet-daemon-perl
  libplrpc-perl libterm-readkey-perl mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server
  mysql-server-5.5 mysql-server-core-5.5
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.8 MB of archives.
After this operation, 96.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://azure.archive.ubuntu.com/ubuntu/ raring/main libaio1 amd64 0.3.109-3 [6,328 B]
Get:2 http://azure.archive.ubuntu.com/ubuntu/ raring-updates/main mysql-common all 5.5.31-0ubuntu0.13.04.1 [13.2 kB]
Get:3 http://azure.archive.ubuntu.com/ubuntu/ raring-updates/main libmysqlclient18 amd64 5.5.31-0ubuntu0.13.04.1 [926 kB]
Get:4 http://azure.archive.ubuntu.com/ubuntu/ raring/main libnet-daemon-perl all 0.48-1 [43.1 kB]
Get:5 http://azure.archive.ubuntu.com/ubuntu/ raring/main libplrpc-perl all 0.2020-2 [36.0 kB]
Get:6 http://azure.archive.ubuntu.com/ubuntu/ raring/main libdbi-perl amd64 1.622-1 [852 kB]
Get:7 http://azure.archive.ubuntu.com/ubuntu/ raring/main libdbd-mysql-perl amd64 4.021-1 [97.7 kB]
Get:8 http://azure.archive.ubuntu.com/ubuntu/ raring-updates/main mysql-client-core-5.5 amd64 5.5.31-0ubuntu0.13.04.1 [1,884 kB]
Get:9 http://azure.archive.ubuntu.com/ubuntu/ raring/main libterm-readkey-perl amd64 2.30-4build4 [28.4 kB]
Get:10 http://azure.archive.ubuntu.com/ubuntu/ raring-updates/main mysql-client-5.5 amd64 5.5.31-0ubuntu0.13.04.1 [8,188 kB]
Get:11 http://azure.archive.ubuntu.com/ubuntu/ raring-updates/main mysql-server-core-5.5 amd64 5.5.31-0ubuntu0.13.04.1 [5,876 kB]
Get:12 http://azure.archive.ubuntu.com/ubuntu/ raring-updates/main mysql-server-5.5 amd64 5.5.31-0ubuntu0.13.04.1 [8,815 kB]
Get:13 http://azure.archive.ubuntu.com/ubuntu/ raring/main libhtml-template-perl all 2.91-1 [65.1 kB]
Get:14 http://azure.archive.ubuntu.com/ubuntu/ raring-updates/main mysql-server all 5.5.31-0ubuntu0.13.04.1 [11.4 kB]
Fetched 26.8 MB in 3s (8,616 kB/s)
Preconfiguring packages ...
Unknown terminal: msys
Check the TERM environment variable.
Also make sure that the terminal is defined in the terminfo database.
Alternatively, set the TERMCAP environment variable to the desired
termcap entry.
debconf: whiptail output the above errors, giving up!
Selecting previously unselected package libaio1:amd64.
(Reading database ... 56764 files and directories currently installed.)
Unpacking libaio1:amd64 (from .../libaio1_0.3.109-3_amd64.deb) ...
Selecting previously unselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.5.31-0ubuntu0.13.04.1_all.deb) ...
Selecting previously unselected package libmysqlclient18:amd64.
Unpacking libmysqlclient18:amd64 (from .../libmysqlclient18_5.5.31-0ubuntu0.13.04.1_amd64.deb) ...
Selecting previously unselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.48-1_all.deb) ...
Selecting previously unselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2020-2_all.deb) ...
Selecting previously unselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.622-1_amd64.deb) ...
Selecting previously unselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.021-1_amd64.deb) ...
Selecting previously unselected package mysql-client-core-5.5.
Unpacking mysql-client-core-5.5 (from .../mysql-client-core-5.5_5.5.31-0ubuntu0.13.04.1_amd64.deb) ...
Selecting previously unselected package libterm-readkey-perl.
Unpacking libterm-readkey-perl (from .../libterm-readkey-perl_2.30-4build4_amd64.deb) ...
Selecting previously unselected package mysql-client-5.5.
Unpacking mysql-client-5.5 (from .../mysql-client-5.5_5.5.31-0ubuntu0.13.04.1_amd64.deb) ...
Selecting previously unselected package mysql-server-core-5.5.
Unpacking mysql-server-core-5.5 (from .../mysql-server-core-5.5_5.5.31-0ubuntu0.13.04.1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mysql-common (5.5.31-0ubuntu0.13.04.1) ...
Selecting previously unselected package mysql-server-5.5.
(Reading database ... 57149 files and directories currently installed.)
Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.31-0ubuntu0.13.04.1_amd64.deb) ...
Unknown terminal: msys
Check the TERM environment variable.
Also make sure that the terminal is defined in the terminfo database.
Alternatively, set the TERMCAP environment variable to the desired
termcap entry.
debconf: whiptail output the above errors, giving up!
dpkg: error processing /var/cache/apt/archives/mysql-server-5.5_5.5.31-0ubuntu0.13.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 255
No apport report written because MaxReports is reached already
Selecting previously unselected package libhtml-template-perl.
Unpacking libhtml-template-perl (from .../libhtml-template-perl_2.91-1_all.deb) ...
Selecting previously unselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.5.31-0ubuntu0.13.04.1_all.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.31-0ubuntu0.13.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I read a post in which I had to install first mysql-common then mysql-server, but I got the same error.

Thank you in advance

---

### Post by neoncyber on 2013-07-16
Hi, I've just solved it, it was because I was using git bash for windows and connected through SSH and nano and other editors doesn't work including the password configuration for mysql. So I just entered from a Linux machine and everything worked like a charm.

---

