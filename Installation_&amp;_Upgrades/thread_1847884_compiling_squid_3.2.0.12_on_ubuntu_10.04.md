---
title: "compiling squid 3.2.0.12 on ubuntu 10.04"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by elico on 2011-09-21
I had a really bad time trying to compile the new squid 3.2.0.12 since version 3.2.0.7 .
there is a bug that caused by squid using some openssl libs during  the compilation.

so in order to compile  squid on Ubuntu server we must first install some packages using:
```
sudo apt-get install build-essential libldap2-dev libpam0g-dev libdb-dev dpatch cdbs libsasl2-dev debhelper libcppunit-dev libkrb5-dev comerr-dev libcap2-dev libexpat1-dev libxml2-dev libcap2-dev dpkg-dev curl libssl-dev libssl0.9.8 libssl0.9.8-dbg libcurl4-openssl-dev
```the above command will install all the necessary  packages for the compilation.
now download the squid tar.bz2 file using the commands

```

cd /opt
mkdir src
cd src
wget http://www.squid-cache.org/Versions/v3/3.2/squid-3.2.0.12.tar.bz2
tar xvjf squid-3.2.0.12.tar.bz2

```get into the the src directory and configure the squid,
i will give an example:
```

cd /opt/src/squid-3.2.0.12
./configure --prefix=/opt/squid32012 --includedir=/include --mandir=/share/man --infodir=/share/info --localstatedir=/opt/squid32012/var --disable-maintainer-mode --disable-dependency-tracking --disable-silent-rules --enable-inline --enable-async-io=8 --enable-storeio=ufs,aufs,diskd --enable-removal-policies=lru,heap --enable-delay-pools --enable-cache-digests --enable-underscores --enable-icap-client --enable-follow-x-forwarded-for --enable-digest-auth-helpers=ldap,password --enable-negotiate-auth-helpers=squid_kerb_auth --enable-external-acl-helpers=ip_user,ldap_group,session,unix_group,wbinfo_group --enable-arp-acl --enable-esi--disable-translation --with-logdir=/opt/squid32012/var/log --with-pidfile=/var/run/squid32012.pid --with-filedescriptors=65536 --with-large-files --with-default-user=proxy --enable-linux-netfilter --enable-ltdl-convenience
(........ a lot of output)
make
(........ a lot of output wil show)
make install
(........ a lot of output)
```also i will link to a init.d script to load squid using my configure.
[squid32012]("http://ec.hadorhabaac.com/squid32012")

in order for squid to work squid effective_cache_user must have full access to log files and cache directory.
dont forget to chagne the cache_dir directive settings in squid.conf

hope it will help anyone.

the config file directives at squid site:
[http://www.squid-cache.org/Doc/config/](http://www.squid-cache.org/Doc/config/)
also very good manual for squid.conf file
[http://www.visolve.com/squid/](http://www.visolve.com/squid/)

---

### Post by elico on 2012-05-22
**an update for ubuntu 12.04**

first you must install then next packages to compile squid:
```
sudo apt-get install build-essential libldap2-dev libpam0g-dev libdb-dev dpatc
h cdbs libsasl2-dev debhelper libcppunit-dev libkrb5-dev comerr-dev libcap2-dev
libexpat1-dev libxml2-dev libcap2-dev dpkg-dev curl libssl-dev libssl1.0.0 libss
l1.0.0-dbg libcurl4-openssl-dev
```download the source tarball from squid-cache site:
```
cd /opt
mkdir src
cd src
wget http://www.squid-cache.org/Versions/v3/3.2/squid-3.2.0.17.tar.bz2
tar xvjf squid-3.2.0.17.tar.bz2
```
then you can user basic configure command:
```
./configure --prefix=/opt/squid32017
```(replace the directory with your preference)

get into squid source directory configure and compile squid using the next command:
```

cd squid-3.2.0.17
./configure --prefix=/opt/squid32017 --with-default-user=proxy
(........ a lot of output)
make
(........ a lot of output wil show)
make install
(........ a lot of output)
chown -R proxy. /opt/squid/var

```this is a basic installation of squid from source.
you can use this init script that was built for squid 32012 and change it a bit for squid32017 in the link:
[http://www1.ngtech.co.il/squid32012](http://www1.ngtech.co.il/squid32012)

another script is a much simpler sh script but has init option to initialize the cachedirs and debug mode to get full output into console:
[http://www1.ngtech.co.il/squid2.initd](http://www1.ngtech.co.il/squid2.initd)

before runing squid make sure that your squid.conf file is properly configured with cache_dir directive.

if you have any problem starting squid you look at cache.log file and move on by the warnings.

if you want some help or consult i am happy to help on squid users mailing lists.
more info on it in: [http://www.squid-cache.org/Support/mailing-lists.html#squid-users](http://www.squid-cache.org/Support/mailing-lists.html#squid-users)

the config file directives at squid site:
[http://www.squid-cache.org/Doc/config/](http://www.squid-cache.org/Doc/config/)

---

### Post by drvirus on 2013-02-15
hi , i want to ask ,
does any one tried to use tproxy mode on squid and succeeded ???


plz advice


regards

---

