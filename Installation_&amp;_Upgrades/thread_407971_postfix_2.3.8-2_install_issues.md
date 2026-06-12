---
title: "postfix 2.3.8-2 install issues"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by fhscobey on 2007-04-12
Getting the following:

*********************************

store01:/etc/apt# sudo apt-get install postfix  
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin resolvconf postfix-cdb
Recommended packages:
  mail-reader
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 0B/1146kB of archives.
After unpacking 2781kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 24031 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.3.8-2_amd64.deb) ...
Setting up postfix (2.3.8-2) ...
Installing new version of config file /etc/init.d/postfix ...
Installing new version of config file /etc/postfix/postfix-script ...
Installing new version of config file /etc/postfix/post-install ...
Installing new version of config file /etc/postfix/postfix-files ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

****************************************

.... and it just hangs there for a long time, until I Ctl+C out, which gives me the following:

^@dpkg: error processing postfix (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)


Got any idea on what to do?

BTW, I ended up here from doing update/upgrade, had issues with the new postfix like above.  Then I removed my old version, and still the new version doesn't want to install.  I'm trying to figure out how I can get the old version back now, I don't know the version number.


My system is:  AMD 64, Ubuntu 6.10.

Thanks!

---

