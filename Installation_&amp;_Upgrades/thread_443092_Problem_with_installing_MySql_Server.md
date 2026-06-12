---
title: "Problem with installing MySql Server"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by Jakachira on 2007-05-14
Firstly, l just want to welcome myself to this great forum.

And, l have a problem with installing MySQL server on my machine. lm using Ubuntu 7.04. l installed it earlier and then removed after l have met some problems. Now l'm trying to install it and getting the following errors. l have tried to upgrade it but to no avail.

root@bobby-desktop:/home/bobby# apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
debconf: Perl may be unconfigured (Can't locate Debconf/Log.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.8.7/i686-linux /opt/lampp/lib/perl5/5.8.7 /opt/lampp/lib/perl5/site_perl/5.8.7/i686-linux /opt/lampp/lib/perl5/site_perl/5.8.7 /opt/lampp/lib/perl5/site_perl .) at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.8.7/i686-linux /opt/lampp/lib/perl5/5.8.7 /opt/lampp/lib/perl5/site_perl/5.8.7/i686-linux /opt/lampp/lib/perl5/site_perl/5.8.7 /opt/lampp/lib/perl5/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server-4.1:
 mysql-server-4.1 depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server-4.1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
 mysql-server-4.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sopan on 2007-06-25
same  problem here, but with server version of ubuntu ...:(

---

