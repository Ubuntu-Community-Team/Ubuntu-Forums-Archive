---
title: "installation BUT instead got Abort?"
date: 2020-10-28
forum: Installation &amp; Upgrades
---

### Post by workaround on 2020-10-28
I tried to do some more installation and instead the system aborted on me?

Need to get 36.3 MB of archives.
After this operation, 274 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Abort.

Why would it do that? Thanks.

---

### Post by CelticWarrior on 2020-10-28
In what context did it happen?
What were you trying to install?

---

### Post by ActionParsnip on 2020-10-28
What is the output of:
```

sudo apt-get update; lsb_release -a; uname -a

```
Thanks

---

### Post by workaround on 2020-10-28
I ran this command: sudo apt install lamp-server^  and that gave me the "Abort".

this below is the output of: sudo apt-get update; lsb_release -a; uname -a

Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [107 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [111 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [98.3 kB]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [24.3 kB]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [56.6 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [229 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [684 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [509 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [205 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [1,768 B]
Fetched 2,028 kB in 1s (1,806 kB/s)                                   
Reading package lists... Done
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal
Linux ichirp 5.4.0-52-generic #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Thanks for your feedback.

---

### Post by uRock on 2020-10-28
Was thinking it might be the command, but it worked for me. At lease until I hit Ctrl+c to kill it.
```
ronnie@TheAngryBalrog:~$ sudo apt install lamp-server^
[sudo] password for ronnie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgssapi3-heimdal' for task 'lamp-server'
Note, selecting 'libhttp-message-perl' for task 'lamp-server'
Note, selecting 'php7.4-cli' for task 'lamp-server'
Note, selecting 'libnghttp2-14' for task 'lamp-server'
Note, selecting 'libencode-locale-perl' for task 'lamp-server'
Note, selecting 'libwind0-heimdal' for task 'lamp-server'
Note, selecting 'mecab-utils' for task 'lamp-server'
Note, selecting 'libsasl2-modules-db' for task 'lamp-server'
Note, selecting 'libcurl4' for task 'lamp-server'
Note, selecting 'libldap-2.4-2' for task 'lamp-server'
Note, selecting 'libapache2-mod-php' for task 'lamp-server'
Note, selecting 'libssh-4' for task 'lamp-server'
Note, selecting 'libevent-core-2.1-7' for task 'lamp-server'
Note, selecting 'php-common' for task 'lamp-server'
Note, selecting 'libaprutil1' for task 'lamp-server'
Note, selecting 'libbrotli1' for task 'lamp-server'
Note, selecting 'php7.4-json' for task 'lamp-server'
Note, selecting 'mysql-client-8.0' for task 'lamp-server'
Note, selecting 'libheimntlm0-heimdal' for task 'lamp-server'
Note, selecting 'mysql-server' for task 'lamp-server'
Note, selecting 'mysql-server-8.0' for task 'lamp-server'
Note, selecting 'libcgi-fast-perl' for task 'lamp-server'
Note, selecting 'libhttp-date-perl' for task 'lamp-server'
Note, selecting 'perl-modules-5.30' for task 'lamp-server'
Note, selecting 'liblwp-mediatypes-perl' for task 'lamp-server'
Note, selecting 'libfcgi-perl' for task 'lamp-server'
Note, selecting 'libmecab2' for task 'lamp-server'
Note, selecting 'libheimbase1-heimdal' for task 'lamp-server'
Note, selecting 'mecab-ipadic-utf8' for task 'lamp-server'
Note, selecting 'libcgi-pm-perl' for task 'lamp-server'
Note, selecting 'libaprutil1-dbd-sqlite3' for task 'lamp-server'
Note, selecting 'libaio1' for task 'lamp-server'
Note, selecting 'libsasl2-2' for task 'lamp-server'
Note, selecting 'libio-html-perl' for task 'lamp-server'
Note, selecting 'ssl-cert' for task 'lamp-server'
Note, selecting 'apache2-data' for task 'lamp-server'
Note, selecting 'php7.4-opcache' for task 'lamp-server'
Note, selecting 'libperl5.30' for task 'lamp-server'
Note, selecting 'libapr1' for task 'lamp-server'
Note, selecting 'libaprutil1-ldap' for task 'lamp-server'
Note, selecting 'libhtml-tagset-perl' for task 'lamp-server'
Note, selecting 'libclone-perl' for task 'lamp-server'
Note, selecting 'librtmp1' for task 'lamp-server'
Note, selecting 'libsasl2-modules' for task 'lamp-server'
Note, selecting 'libprotobuf-lite23' for task 'lamp-server'
Note, selecting 'mysql-client-core-8.0' for task 'lamp-server'
Note, selecting 'php7.4-mysql' for task 'lamp-server'
Note, selecting 'libldap-common' for task 'lamp-server'
Note, selecting 'libhcrypto4-heimdal' for task 'lamp-server'
Note, selecting 'php7.4-readline' for task 'lamp-server'
Note, selecting 'liblua5.2-0' for task 'lamp-server'
Note, selecting 'mysql-common' for task 'lamp-server'
Note, selecting 'libsodium23' for task 'lamp-server'
Note, selecting 'libhtml-template-perl' for task 'lamp-server'
Note, selecting 'mecab-ipadic' for task 'lamp-server'
Note, selecting 'libtimedate-perl' for task 'lamp-server'
Note, selecting 'libroken18-heimdal' for task 'lamp-server'
Note, selecting 'apache2-bin' for task 'lamp-server'
Note, selecting 'perl' for task 'lamp-server'
Note, selecting 'libasn1-8-heimdal' for task 'lamp-server'
Note, selecting 'libkrb5-26-heimdal' for task 'lamp-server'
Note, selecting 'php7.4-common' for task 'lamp-server'
Note, selecting 'libjansson4' for task 'lamp-server'
Note, selecting 'libgdbm-compat4' for task 'lamp-server'
Note, selecting 'apache2' for task 'lamp-server'
Note, selecting 'php-mysql' for task 'lamp-server'
Note, selecting 'apache2-utils' for task 'lamp-server'
Note, selecting 'libhx509-5-heimdal' for task 'lamp-server'
Note, selecting 'libhtml-parser-perl' for task 'lamp-server'
Note, selecting 'libapache2-mod-php7.4' for task 'lamp-server'
Note, selecting 'liburi-perl' for task 'lamp-server'
Note, selecting 'mysql-server-core-8.0' for task 'lamp-server'
libasn1-8-heimdal is already the newest version (7.7.0+dfsg-2).
libasn1-8-heimdal set to manually installed.
libbrotli1 is already the newest version (1.0.9-2).
libbrotli1 set to manually installed.
libclone-perl is already the newest version (0.45-1).
libclone-perl set to manually installed.
libcurl4 is already the newest version (7.68.0-1ubuntu4).
libcurl4 set to manually installed.
libencode-locale-perl is already the newest version (1.05-1).
libencode-locale-perl set to manually installed.
libgdbm-compat4 is already the newest version (1.18.1-5.1).
libgdbm-compat4 set to manually installed.
libgssapi3-heimdal is already the newest version (7.7.0+dfsg-2).
libgssapi3-heimdal set to manually installed.
libhcrypto4-heimdal is already the newest version (7.7.0+dfsg-2).
libhcrypto4-heimdal set to manually installed.
libheimbase1-heimdal is already the newest version (7.7.0+dfsg-2).
libheimbase1-heimdal set to manually installed.
libheimntlm0-heimdal is already the newest version (7.7.0+dfsg-2).
libheimntlm0-heimdal set to manually installed.
libhtml-parser-perl is already the newest version (3.73-1).
libhtml-parser-perl set to manually installed.
libhtml-tagset-perl is already the newest version (3.20-4).
libhtml-tagset-perl set to manually installed.
libhttp-date-perl is already the newest version (6.05-1).
libhttp-date-perl set to manually installed.
libhttp-message-perl is already the newest version (6.25-1).
libhttp-message-perl set to manually installed.
libhx509-5-heimdal is already the newest version (7.7.0+dfsg-2).
libhx509-5-heimdal set to manually installed.
libio-html-perl is already the newest version (1.001-1).
libio-html-perl set to manually installed.
libjansson4 is already the newest version (2.13.1-1ubuntu1).
libjansson4 set to manually installed.
libkrb5-26-heimdal is already the newest version (7.7.0+dfsg-2).
libkrb5-26-heimdal set to manually installed.
libldap-2.4-2 is already the newest version (2.4.53+dfsg-1ubuntu1).
libldap-2.4-2 set to manually installed.
libldap-common is already the newest version (2.4.53+dfsg-1ubuntu1).
libldap-common set to manually installed.
liblua5.2-0 is already the newest version (5.2.4-1.1build3).
liblua5.2-0 set to manually installed.
liblwp-mediatypes-perl is already the newest version (6.04-1).
liblwp-mediatypes-perl set to manually installed.
libnghttp2-14 is already the newest version (1.41.0-3).
libnghttp2-14 set to manually installed.
libperl5.30 is already the newest version (5.30.3-4).
libperl5.30 set to manually installed.
libprotobuf-lite23 is already the newest version (3.12.3-2ubuntu2).
libprotobuf-lite23 set to manually installed.
libroken18-heimdal is already the newest version (7.7.0+dfsg-2).
libroken18-heimdal set to manually installed.
librtmp1 is already the newest version (2.4+20151223.gitfa8646d.1-2build2).
librtmp1 set to manually installed.
libsasl2-2 is already the newest version (2.1.27+dfsg-2ubuntu1).
libsasl2-2 set to manually installed.
libsasl2-modules is already the newest version (2.1.27+dfsg-2ubuntu1).
libsasl2-modules set to manually installed.
libsasl2-modules-db is already the newest version (2.1.27+dfsg-2ubuntu1).
libsasl2-modules-db set to manually installed.
libsodium23 is already the newest version (1.0.18-1).
libsodium23 set to manually installed.
libssh-4 is already the newest version (0.9.4-1ubuntu3).
libssh-4 set to manually installed.
libtimedate-perl is already the newest version (2.3300-1).
libtimedate-perl set to manually installed.
liburi-perl is already the newest version (1.76-2).
liburi-perl set to manually installed.
libwind0-heimdal is already the newest version (7.7.0+dfsg-2).
libwind0-heimdal set to manually installed.
mysql-common is already the newest version (5.8+1.0.5ubuntu2).
mysql-common set to manually installed.
perl is already the newest version (5.30.3-4).
perl set to manually installed.
perl-modules-5.30 is already the newest version (5.30.3-4).
perl-modules-5.30 set to manually installed.
ssl-cert is already the newest version (1.0.39).
ssl-cert set to manually installed.
Suggested packages:
  apache2-doc apache2-suexec-pristine | apache2-suexec-custom php-pear libipc-sharedcache-perl mailx tinyca
The following NEW packages will be installed:
  apache2 apache2-bin apache2-data apache2-utils libaio1 libapache2-mod-php libapache2-mod-php7.4 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap
  libcgi-fast-perl libcgi-pm-perl libevent-core-2.1-7 libfcgi-perl libhtml-template-perl libmecab2 mecab-ipadic mecab-ipadic-utf8 mecab-utils mysql-client-8.0
  mysql-client-core-8.0 mysql-server mysql-server-8.0 mysql-server-core-8.0 php-common php-mysql php7.4-cli php7.4-common php7.4-json php7.4-mysql php7.4-opcache
  php7.4-readline
0 upgraded, 33 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.6 MB of archives.
After this operation, 269 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 libapr1 amd64 1.6.5-1ubuntu1 [91.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 libaprutil1 amd64 1.6.1-4ubuntu2 [84.7 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 libaprutil1-dbd-sqlite3 amd64 1.6.1-4ubuntu2 [10.5 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 libaprutil1-ldap amd64 1.6.1-4ubuntu2 [8,736 B]
Get:5 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 apache2-bin amd64 2.4.46-1ubuntu1 [1,204 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 apache2-data all 2.4.46-1ubuntu1 [158 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 apache2-utils amd64 2.4.46-1ubuntu1 [83.6 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 apache2 amd64 2.4.46-1ubuntu1 [95.6 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 mysql-client-core-8.0 amd64 8.0.21-1 [4,189 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 mysql-client-8.0 amd64 8.0.21-1 [22.0 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 libaio1 amd64 0.3.112-8 [7,488 B]
Get:12 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 libevent-core-2.1-7 amd64 2.1.12-stable-1 [89.4 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 libmecab2 amd64 0.996-14 [233 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu groovy/main amd64 mysql-server-core-8.0 amd64 8.0.21-1 [16.9 MB]
28% [14 mysql-server-core-8.0 2,598 kB/16.9 MB 15%]^C
ronnie@TheAngryBalrog:~$ 

```

---

### Post by workaround on 2020-10-28
OK, I ran the command again and it worked, still working.  Thanks

---

