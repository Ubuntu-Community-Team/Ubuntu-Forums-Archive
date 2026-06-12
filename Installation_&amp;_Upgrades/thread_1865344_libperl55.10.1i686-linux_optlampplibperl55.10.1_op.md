---
title: "/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_pe"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by csayantan on 2011-10-20
Hi 

I am getting this error.kindly help...

```

root@dba:/opt/mysql/mysql-5.5.16# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libcurl3 libnspr4-0d libnss3 libnss3-1d
The following NEW packages will be installed:
  libcurl3 libnspr4-0d libnss3-1d
The following packages will be upgraded:
  libnss3
1 upgraded, 3 newly installed, 0 to remove and 131 not upgraded.
8 not fully installed or removed.
Need to get 240 kB/1,523 kB of archives.
After this operation, 733 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://in.archive.ubuntu.com/ubuntu/ natty/universe libnspr4-0d amd64 4.8.7-0ubuntu1 [13.8 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ natty-updates/main libcurl3 amd64 7.21.3-1ubuntu1.3 [226 kB]
Fetched 240 kB in 2s (85.6 kB/s)   
debconf: Perl may be unconfigured (Can't locate Debconf/Log.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_perl/5.10.1/i686-linux /opt/lampp/lib/perl5/site_perl/5.10.1 .) at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Selecting previously deselected package libnspr4-0d.
(Reading database ... 155894 files and directories currently installed.)
Unpacking libnspr4-0d (from .../libnspr4-0d_4.8.7-0ubuntu1_amd64.deb) ...
Preparing to replace libnss3 3.12.9+ckbi-1.82-0ubuntu2 (using .../libnss3_3.12.9+ckbi-1.82-0ubuntu2.1_amd64.deb) ...
Unpacking replacement libnss3 ...
Selecting previously deselected package libnss3-1d.
Unpacking libnss3-1d (from .../libnss3-1d_3.12.9+ckbi-1.82-0ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libcurl3.
Unpacking libcurl3 (from .../libcurl3_7.21.3-1ubuntu1.3_amd64.deb) ...
Setting up tzdata (2011j-0ubuntu0.11.04) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_perl/5.10.1/i686-linux /opt/lampp/lib/perl5/site_perl/5.10.1 .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libnspr4-0d (4.8.7-0ubuntu1) ...
Setting up libnss3 (3.12.9+ckbi-1.82-0ubuntu2.1) ...
Setting up libnss3-1d (3.12.9+ckbi-1.82-0ubuntu2.1) ...
Setting up libcurl3 (7.21.3-1ubuntu1.3) ...
Setting up google-chrome-stable (14.0.835.186-r101821) ...
update-alternatives: using /usr/bin/google-chrome to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/google-chrome to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
Setting up man-db (2.5.9-4) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_perl/5.10.1/i686-linux /opt/lampp/lib/perl5/site_perl/5.10.1 .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up mono-apache-server2 (2.6.5-3) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_perl/5.10.1/i686-linux /opt/lampp/lib/perl5/site_perl/5.10.1 .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing mono-apache-server2 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mono-apache-server:
 mono-apache-server depends on mono-apache-server2 (= 2.6.5-3); however:
  Package mono-apache-server2 is not configured yet.
dpkg: error processing mono-apache-server (--configure):
 dependency problems - leaving unconfigured
Setting up mono-apache-server1 (2.6.5-3) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_perl/5.10.1/i686-linux /opt/lampp/lib/perl5/site_perl/5.10.1 .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing mono-apache-server1 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libapache2-mod-mono:
 libapache2-mod-mono depends on mono-apache-server (>= 2.6.5) | mono-apache-server2 (>= 2.6.5) | mono-apache-server1 (>= 2.6.5); however:
  Package mono-apache-server is not configured yet.
  Package mono-apache-server2 is not configured yet.
  Package mono-apache-server1 is not configured yet.
 libapache2-mod-mono depends on mono-apache-server (<< 2.6.6) | mono-apache-server2 (<< 2.6.6) | mono-apache-server1 (<< 2.6.6); however:
  Package mono-apache-server is not configured yet.
  Package mono-apache-server2 is not configured yet.
  Package mono-apache-server1 is not configured yet.
dpkg: error processing libapache2-mod-mono (--configure):
 dependency problems - leaving unconfigured
Setting up sysstat (9.1.7-2ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              Can't locate Debconf/Db.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_perl/5.10.1/i686-linux /opt/lampp/lib/perl5/site_perl/5.10.1 .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing sysstat (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 tzdata
 man-db
 mono-apache-server2
 mono-apache-server
 mono-apache-server1
 libapache2-mod-mono
 sysstat
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@dba:/opt/mysql/mysql-5.5.16# apt-get install cmake
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cmake-data libxmlrpc-core-c3-0
The following NEW packages will be installed:
  cmake cmake-data libxmlrpc-core-c3-0
0 upgraded, 3 newly installed, 0 to remove and 131 not upgraded.
7 not fully installed or removed.
Need to get 4,889 kB of archives.
After this operation, 14.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://in.archive.ubuntu.com/ubuntu/ natty/main libxmlrpc-core-c3-0 amd64 1.16.32-0ubuntu3 [118 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ natty/main cmake-data all 2.8.3-3ubuntu7 [637 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ natty/main cmake amd64 2.8.3-3ubuntu7 [4,135 kB]
Fetched 4,889 kB in 24s (199 kB/s)                                                                                                                           
debconf: Perl may be unconfigured (Can't locate Debconf/Log.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_perl/5.10.1/i686-linux /opt/lampp/lib/perl5/site_perl/5.10.1 .) at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Setting up tzdata (2011j-0ubuntu0.11.04) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /opt/lampp/lib/perl5/5.10.1/i686-linux /opt/lampp/lib/perl5/5.10.1 /opt/lampp/lib/perl5/site_perl/5.10.1/i686-linux /opt/lampp/lib/perl5/site_perl/5.10.1 .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@dba:/opt/mysql/mysql-5.5.16# cmake .
The program 'cmake' is currently not installed.  You can install it by typing:
apt-get install cmake
root@dba:/opt/mysql/mysql-5.5.16# 


``````

root@dba:/opt/mysql/mysql-5.5.16# uname -a 
Linux dba 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
root@dba:/opt/mysql/mysql-5.5.16# 


```
Another problem is that i can not install any package from GUI tools.its always report for authantication failure.
NB:-I always change my password using passwd command.is that wrong any?
kind regards

---

### Post by directhex on 2011-10-20
Your system seems to be using a nonstandard Perl which isn't looking in the system Perl folders for Perl modules. As a result, any Debian package using debconf is failing to install, since debconf isn't found by your nonstandard perl.

---

### Post by csayantan on 2011-10-25
> **directhex said:**
> Your system seems to be using a nonstandard Perl which isn't looking in the system Perl folders for Perl modules. As a result, any Debian package using debconf is failing to install, since debconf isn't found by your nonstandard perl.

can you please suggest how to avail this non - standered perl to the system so that dbconfig can find it??

kind regards

---

### Post by directhex on 2011-10-26
You should check your $PATH variable, and remove nonstandard entries.

If you don't know what you're doing, $PATH should be /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by csayantan on 2011-10-26
> **directhex said:**
> You should check your $PATH variable, and remove nonstandard entries.

If you don't know what you're doing, $PATH should be /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

problem is that i need to use lampp for my PHP coding.and my coligue configured it.he made a link to lammp/bin/perl.so i removed the perl file from /usr/bin/perl and made an installation of perl-base again but that perl version is 5.12.x.now the whole system has changed AND my current unity desktop is not comming at all.only thing is alive is ctrl+ALT+F2 WITHOUT ANY GRAPHICS SUPPORT to go-to command prompt so that i get some prompt.please solve this problem.can you just give me proper package which actually solve all the issue.

My another problem is that i can not use apt-get install option to run the whole thing.so i ask for wget (link to proper package) to install and solve the whole thing.
:popcorn:
kind regards

---

### Post by csayantan on 2011-10-27
work around was :
```

apt-get -f install



```fixed all the issue.
but there is a problem i can start unity by:
```

unity --reset

```
but its not automated at all.each time after login i need to start it.
issue 1)is there any option to make it automated??
AND 
issue 2) I can not login using GUI during installation of software.how can i fix this issue.


kind regards

---

