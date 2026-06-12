---
title: "Uninstall Zend Server 5.0"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by akril on 2010-06-22
Hi. I have Ubuntu 10.04. 

I had installed **Zend Server 5.0.** Later, after some updates, I think, it started to work incorrectly:

[LIST]
[*]zendctl didn't control server. It didn't stop or start it. Apache became autonomous
[*][http://localhost:10081/ZendServer/](http://localhost:10081/ZendServer/) responded "Can't connect" in browser while [http://localhost](http://localhost) (apache) was working well.
[*]On system reboot, the whole reboot proces freezed after "Stopping Zend Server"
[/LIST]
So I decided to reinstall Zend Server

But command
[B]# aptitude purge '~nzend.* '
[/B]didn't finish correctly as there were problems with packages 
[B]jobqueue-zend-server 
[/B]and 
[B]help-zend-server

[/B]And now the command[B]

sudo aptitude -f install[/B]

results in 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  apache2-mpm-prefork{u} apache2-utils{u} apache2.2-bin{u} 
  apache2.2-common{u} jobqueue-zend-server{p} jq-daemon-zend-server{u} 
  libaio1{u} libapache2-mod-php-5.3-zend-server{u} libapr1{u} 
  libaprutil1{u} libaprutil1-dbd-sqlite3{u} libaprutil1-ldap{u} 
  libframework1-zend-server{u} libicu36{u} libkrb53{u} libmcrypt4{u} 
  liboci-us-locales-zend{u} libpng3{u} libpq4{u} lighttpd-zend-server{u} 
  php-5.3-bcmath-zend-server{u} php-5.3-bz2-zend-server{u} 
  php-5.3-calendar-zend-server{u} php-5.3-code-tracing-zend-server{u} 
  php-5.3-common-extensions-zend-server{u} php-5.3-ctype-zend-server{u} 
  php-5.3-curl-zend-server{u} php-5.3-data-cache-zend-server{u} 
  php-5.3-debugger-zend-server{u} php-5.3-dev-zend-server{u} 
  php-5.3-exif-zend-server{u} php-5.3-fcgi-zend-server{u} 
  php-5.3-fileinfo-zend-server{u} php-5.3-ftp-zend-server{u} 
  php-5.3-gd-zend-server{u} php-5.3-gettext-zend-server{u} 
  php-5.3-gui-zend-server{u} php-5.3-imap-zend-server{u} 
  php-5.3-intl-zend-server{u} php-5.3-jq-zend-server{u} 
  php-5.3-json-zend-server{u} php-5.3-ldap-zend-server{u} 
  php-5.3-mbstring-zend-server{u} php-5.3-mcrypt-zend-server{u} 
  php-5.3-monitor-ui-zend-server{u} php-5.3-monitor-zend-server{u} 
  php-5.3-mysql-zend-server{u} php-5.3-mysqli-zend-server{u} 
  php-5.3-oci8-zend-server{u} php-5.3-optimizer-plus-zend-server{u} 
  php-5.3-page-cache-zend-server{u} php-5.3-pdo-mysql-zend-server{u} 
  php-5.3-pdo-oci-zend-server{u} php-5.3-pdo-pgsql-zend-server{u} 
  php-5.3-pgsql-zend-server{u} php-5.3-phar-zend-server{u} 
  php-5.3-posix-zend-server{u} php-5.3-sc-zend-server{u} 
  php-5.3-session-clustering-zend-server{u} php-5.3-soap-zend-server{u} 
  php-5.3-sockets-zend-server{u} php-5.3-sqlite-zend-server{u} 
  php-5.3-tidy-zend-server{u} php-5.3-tokenizer-zend-server{u} 
  php-5.3-xmlreader-zend-server{u} php-5.3-xmlwriter-zend-server{u} 
  php-5.3-xsl-zend-server{u} php-5.3-zds-zend-server{u} 
  php-5.3-zem-zend-server{u} php-5.3-zend-extensions{u} 
  php-5.3-zendutils-zend-server{u} php-5.3-zip-zend-server{u} 
  sc-daemon-zend-server{u} zend-base{u} zend-server-doc{u} 
  zend-server-framework{u} zend-server-php-5.3{a} 
0 packages upgraded, 0 newly installed, 77 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 257MB will be freed.
Do you want to continue? [Y/n/?] Y 
(Reading database ... 145444 files and directories currently installed.)
Removing zend-server-php-5.3 ...
Stopping Zend Server 5.0 ..

E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of jobqueue-zend-server:
 jobqueue-zend-server depends on jq-daemon-zend-server; however:
  Package jq-daemon-zend-server is not configured yet.
dpkg: error processing jobqueue-zend-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 jobqueue-zend-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```and command:

**sudo dpkg --configure -a**

```

dpkg: dependency problems prevent configuration of jobqueue-zend-server:
 jobqueue-zend-server depends on jq-daemon-zend-server; however:
  Package jq-daemon-zend-server is not configured yet.
dpkg: error processing jobqueue-zend-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 jobqueue-zend-server

```And I still can't stop ZendServer. I can stop only it's web services separately. 

P.S. I'm neewbie in Ubuntu :)

P.S.S.  I found a guy asking about the same problem at [Zend Forum]("http://forums.zend.com/viewtopic.php?f=8&t=4309&start=0") but nobody seems to help him.

---

### Post by DonMostro on 2010-07-26
Dude i got exactly the same problem, nothing works, I just wanna remove zend-server and work with Apache. I think was a big mistake to install it.
After i install zend-server-phpmyadmin have all dpkg system ruined for dependences problems. This is weird.

---

### Post by DonMostro on 2010-07-26
Uff i solved following this topic [http://forums.zend.com/viewtopic.php?f=8&t=4550](http://forums.zend.com/viewtopic.php?f=8&t=4550) and i not pretend to install Zend Server again (at least not by repos), Now im deleting the repos. 

i got the same problem twice and now was in a fresh installation (Kubuntu 10.04).  .deb installation of zend-server-ce is very dirty and buggie, now i had no doubt about it.

the worst problem i had was that zend-server hangs the system when i tried to shut down, in the past i dont know reason of this problem, now i know was zend-server the cause, because uninstalling zend-server everything backs to normal. So i kill two bird in one shoot.

is a pity that so badly run zend-server-ce in ubuntu.

---

