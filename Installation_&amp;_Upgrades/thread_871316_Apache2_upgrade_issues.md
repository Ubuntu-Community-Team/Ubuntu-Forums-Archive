---
title: "Apache2 upgrade issues"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by 3D Peruna on 2008-07-26
Recently tried to from Edge to Fiesty.  Did the apt-get upgrades, apt-get update.  Ending up with this error and I can't seem to locate a solution to it.

[INDENT][I]root@server:/home/server# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  apache2: Depends: apache2-mpm-worker (>= 2.2.3-3.2build1) but it is not installed or
                    apache2-mpm-prefork (>= 2.2.3-3.2build1) but 2.0.55-4ubuntu4.1 is installed or
                    apache2-mpm-event (>= 2.2.3-3.2build1) but it is not installed
  libapache2-mod-php5: Depends: apache2.2-common but it is not installed
E: Unmet dependencies. Try using -f.
root@server:/home/server# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmail-spf-query-perl gettext libnet-cidr-lite-perl mono-classlib-1.0 mono-classlib-2.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5-cli php5-common php5-curl php5-gd php5-ldap
  php5-mhash php5-mysql php5-pspell php5-snmp php5-sqlite php5-xmlrpc php5-xsl
The following packages will be REMOVED:
  apache2-common
The following NEW packages will be installed:
  apache2.2-common
The following packages will be upgraded:
  apache2-mpm-prefork libapache2-mod-php5 php5-cli php5-common php5-curl php5-gd php5-ldap php5-mhash php5-mysql
  php5-pspell php5-snmp php5-sqlite php5-xmlrpc php5-xsl
14 upgraded, 1 newly installed, 1 to remove and 132 not upgraded.
2 not fully installed or removed.
Need to get 0B/6885kB of archives.
After unpacking 610kB of additional disk space will be used.
Do you want to continue [Y/n]? y
[COLOR="Red"][B]dpkg: apache2-common: dependency problems, but removing anyway as you request:
 apache2-mpm-prefork depends on apache2-common (= 2.0.55-4ubuntu4.1).
(Reading database ... 29156 files and directories currently installed.)
Removing apache2-common ...
 * Stopping apache 2.0 web server...                                                                        [fail]
invoke-rc.d: initscript apache2, action "stop" failed.
dpkg: error processing apache2-common (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 apache2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server:/home/server#[/B][/COLOR][/I][/INDENT]

Help?!?

---

