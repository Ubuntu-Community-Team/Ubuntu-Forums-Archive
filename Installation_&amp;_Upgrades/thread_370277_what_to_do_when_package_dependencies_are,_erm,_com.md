---
title: "what to do when package dependencies are, erm, compromised?"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by danmcb on 2007-02-25
I generally use synaptic to install new packages (except perl which I do via cpan)

I have a problem that the dependency tree seems broken, I cannot install some new things and if I use either synaptic or apt to try to install/reinstall the things which are reported as being in error, it fails (dpkg returns some error, apparently)

how do I go about repairing?

I have 6.06 running under vmware as a guest on a win xp system. It's nice!

thanks

Daniel

---

### Post by bapoumba on 2007-02-25
Hi,
could you post the complete error message to **sudo aptitude update**?
And BTW, please edit your title ;)

---

### Post by danmcb on 2007-02-26
ah yes, sorry about that - title altered :) 

thanks - here it is

root@daniel-ubuntu:~# aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 5B in 18s (0B/s)
Reading package lists... Done

---

### Post by danmcb on 2007-02-26
here is the problem itself (lots of output - sorry)

it could be due that I have built apache2/perl/mod_perl from scratch, which apt won't know about? but none of those are mentioned in the error ...

root@daniel-ubuntu:~# apt-get install libapache2-mod-fcgid
Reading package lists... Done
Building dependency tree... Done
libapache2-mod-fcgid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
35 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
debconf: Perl may be unconfigured (Can't locate Debconf/Log.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .) at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Setting up lvm2 (2.02.02-1ubuntu1) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing lvm2 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up screen (4.0.2-4.1ubuntu5) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing screen (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libssl0.9.8 (0.9.8a-7ubuntu0.3) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing libssl0.9.8 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdns21:
 libdns21 depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libdns21 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libisccfg1:
 libisccfg1 depends on libdns21; however:
  Package libdns21 is not configured yet.
dpkg: error processing libisccfg1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbind9-0:
 libbind9-0 depends on libdns21; however:
  Package libdns21 is not configured yet.
 libbind9-0 depends on libisccfg1; however:
  Package libisccfg1 is not configured yet.
dpkg: error processing libbind9-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libbind9-0; however:
  Package libbind9-0 is not configured yet.
 bind9-host depends on libdns21; however:
  Package libdns21 is not configured yet.
 bind9-host depends on libisccfg1; however:
  Package libisccfg1 is not configured yet.
 bind9-host depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing bind9-host (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libbind9-0; however:
  Package libbind9-0 is not configured yet.
 dnsutils depends on libdns21; however:
  Package libdns21 is not configured yet.
 dnsutils depends on libisccfg1; however:
  Package libisccfg1 is not configured yet.
 dnsutils depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
 dnsutils depends on bind9-host | host; however:
  Package bind9-host is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not configured yet.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssh-client:
 openssh-client depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing openssh-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of w3m:
 w3m depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing w3m (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing openssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2-utils:
 apache2-utils depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing apache2-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2-common:
 apache2-common depends on openssl; however:
  Package openssl is not configured yet.
 apache2-common depends on apache2-utils (= 2.0.55-4ubuntu2.1); however:
  Package apache2-utils is not configured yet.
dpkg: error processing apache2-common (--configure):
 dependency problems - leaving unconfigured
Setting up gdm (2.14.10-0ubuntu1.1) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 2
Setting up hal (0.5.7-1ubuntu18.2) ...
Can't locate Debian/AdduserCommon.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .) at /usr/sbin/adduser line 34.
BEGIN failed--compilation aborted at /usr/sbin/adduser line 34.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python2.4-dbus:
 python2.4-dbus depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on python2.4; however:
  Package python2.4 is not configured yet.
 hal-device-manager depends on python2.4-dbus (>= 0.60); however:
  Package python2.4-dbus is not configured yet.
 hal-device-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-fcgid:
 libapache2-mod-fcgid depends on apache2-common; however:
  Package apache2-common is not configured yet.
dpkg: error processing libapache2-mod-fcgid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpq4:
 libpq4 depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libpq4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl0.9.8 (= 0.9.8a-7ubuntu0.3); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpq-dev:
 libpq-dev depends on libpq4 (= 8.1.8-0ubuntu6.06.1); however:
  Package libpq4 is not configured yet.
 libpq-dev depends on libssl-dev; however:
  Package libssl-dev is not configured yet.
dpkg: error processing libpq-dev (--configure):
 dependency problems - leaving unconfigured
Setting up mozilla-browser (1.7.12-1.1ubuntu2) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing mozilla-browser (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mozilla-cascades:
 mozilla-cascades depends on mozilla-browser (>= 2:1.0.0); however:
  Package mozilla-browser is not configured yet.
dpkg: error processing mozilla-cascades (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-client-8.1:
 postgresql-client-8.1 depends on libpq4 (>= 8.1.4); however:
  Package libpq4 is not configured yet.
 postgresql-client-8.1 depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing postgresql-client-8.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-8.1:
 postgresql-8.1 depends on libpq4 (>= 8.1.4); however:
  Package libpq4 is not configured yet.
 postgresql-8.1 depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
 postgresql-8.1 depends on postgresql-client-8.1; however:
  Package postgresql-client-8.1 is not configured yet.
dpkg: error processing postgresql-8.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-plperl-8.1:
 postgresql-plperl-8.1 depends on postgresql-8.1; however:
  Package postgresql-8.1 is not configured yet.
dpkg: error processing postgresql-plperl-8.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-server-dev-8.1:
 postgresql-server-dev-8.1 depends on libpq-dev (>= 8.1); however:
  Package libpq-dev is not configured yet.
dpkg: error processing postgresql-server-dev-8.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on python2.4 (>= 2.3.90); however:
  Package python2.4 is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-examples:
 python2.4-examples depends on python2.4 (>= 2.4.3-0ubuntu6); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-examples (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gdbm:
 python2.4-gdbm depends on python2.4 (= 2.4.3-0ubuntu6); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-gdbm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-tk:
 python2.4-tk depends on python2.4 (= 2.4.3-0ubuntu6); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-tk (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (3.0.22-1ubuntu3.2) ...
Can't locate Debconf/Db.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/i686-linux-thread-multi /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.22-1ubuntu3.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh-askpass-gnome:
 ssh-askpass-gnome depends on openssh-client | ssh (>= 1:1.2pre7-4) | ssh-krb5; however:
  Package openssh-client is not configured yet.
  Package ssh is not installed.
  Package ssh-krb5 is not installed.
dpkg: error processing ssh-askpass-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lvm2
 screen
 libssl0.9.8
 python2.4
 libdns21
 libisccfg1
 libbind9-0
 bind9-host
 dnsutils
 openssh-client
 w3m
 openssl
 apache2-utils
 apache2-common
 gdm
 hal
 python2.4-dbus
 hal-device-manager
 libapache2-mod-fcgid
 libpq4
 libssl-dev
 libpq-dev
 mozilla-browser
 mozilla-cascades
 postgresql-client-8.1
 postgresql-8.1
 postgresql-plperl-8.1
 postgresql-server-dev-8.1
 python-uno
 python2.4-examples
 python2.4-gdbm
 python2.4-tk
 samba-common
 smbclient
 ssh-askpass-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@daniel-ubuntu:~#

---

### Post by bapoumba on 2007-02-26
> **danmcb said:**
> here is the problem itself (lots of output - sorry)

it could be due that I have built apache2/perl/mod_perl from scratch, which apt won't know about? but none of those are mentioned in the error ...

May be. Not sure what to recommend. I've looked around, but did not find anything convincing.
```
sudo dpkg --configure -a
```
?

edit: thanks for changing the title ;)
I went ahead and changed the main title and all the other posts titles accordingly.

---

### Post by danmcb on 2007-02-27
ok. thanks for looking. that command gives the same set of errors BTW.

---

### Post by bapoumba on 2007-02-27
Could you please post your sources.list (**cat /etc/apt/sources.list**)?

---

