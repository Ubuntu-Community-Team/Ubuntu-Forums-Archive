---
title: "Help repairing a new install"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by rudy7 on 2015-09-25
Firstly, I am new to ubuntu (linux in general) and I appreciate any help or advice on my problem.

I installed 14.04 according to this tutorial: [https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3](https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3)

All went well and I was able to begin working on a website.

I then attempted to install a package that failed and after a reboot, several things stopped working, namely: MySql and php.

Also during reboot "ClamAv" fails as does "stopping cold plug devices".

After logging in I try to run "sudo apt-get install -f" and I get

Reading changelogs... Done
Preconfiguring packages ...
(Reading database ... 137843 files and directories currently installed.)
Removing cloud-init (0.7.5-0ubuntu1.10) ...
dpkg: error processing package cloud-init (--remove):
 cannot remove `/usr/lib/cloud-init/write-ssh-key-fingerprints': Permission denied
Removing postfix-mysql (2.11.0-1ubuntu1) ...
dpkg: error processing package postfix-mysql (--remove):
 cannot remove `/usr/lib/postfix/dict_mysql.so': Permission denied
Removing software-properties-common (0.92.37.3) ...
/var/lib/dpkg/info/software-properties-common.prerm: /usr/bin/py3clean: /usr/bin/python3: bad interpreter: No such file or directory
dpkg: error processing package software-properties-common (--remove):
 subprocess installed pre-removal script returned error exit status 126
/var/lib/dpkg/info/software-properties-common.postinst: /usr/bin/py3compile: /usr/bin/python3: bad interpreter: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 cloud-init
 postfix-mysql
 software-properties-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bucky Ball on 2015-09-25
Welcome. Please try:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

This will NOT upgrade you Ubuntu install to a newer release. Please post any and all errors.

---

### Post by rudy7 on 2015-09-25
Thank you,

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libacl1:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libattr1:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libbz2-1.0:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libcap2:i386 : Depends: libc6:i386 (>= 2.8) but it is not installed
 libclass-dbi-mysql-perl : Depends: libdbd-mysql-perl but it is not installed
 libcomerr2:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libdb5.3:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libdbus-1-3:i386 : Depends: libc6:i386 (>= 2.10) but it is not installed
 libdrm2:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libjson-c2:i386 : Depends: libc6:i386 (>= 2.8) but it is not installed
 liblzma5:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libmysqlclient18 : Depends: mysql-common (>= 5.5.44-0ubuntu0.14.04.1) but it is
 libtinfo5:i386 : Depends: libc6:i386 (>= 2.15) but it is not installed
 mysql-server-5.5 : Depends: mysql-client-5.5 (>= 5.5.44-0ubuntu0.14.04.1) but i
                    Depends: mysql-server-core-5.5 (>= 5.5.44-0ubuntu0.14.04.1)
                    PreDepends: mysql-common (>= 5.5.44-0ubuntu0.14.04.1) but it
 php-auth : Depends: php-pear (>= 1.4.0~b1) but it is not installed
            Recommends: php-file-passwd (>= 1.1.0) but it is not installable
            Recommends: php-net-pop3 (>= 1.3.0) but it is not installable
            Recommends: php-mdb but it is not installable
            Recommends: php-auth-radius but it is not installable
            Recommends: php-crypt-chap (>= 1.0.0) but it is not installable
            Recommends: php-file-smbpasswd (>= 1.0.0) but it is not installable
            Recommends: php-http-client (>= 1.1.0) but it is not installable
            Recommends: php-net-vpopmaild (>= 0.1.0) but it is not installable
            Recommends: php5-vpopmail (>= 0.2) but it is not installable
            Recommends: php5-kadm5 (>= 0.2.3) but it is not installable
            Recommends: php5-saprfc but it is not installable
 php-auth-sasl : Depends: php5 (>= 4.2.0) but it is not installed
                 Depends: php-pear (>= 1.4.3) but it is not installed
 php-db : Depends: php-pear but it is not installed
 php-gettext : Depends: php5 but it is not installed or
                        php5-cli but it is not installed
 php-http-request : PreDepends: php-pear (>= 5.3) but it is not installed
 php-log : Depends: php5 (>= 5.0.0) but it is not installed
           Depends: php-pear (>= 1.4.3) but it is not installed
           Recommends: php5-sqlite but it is not installed
 php-mail : Depends: php-pear (>= 1.5.6) but it is not installed
 php-mail-mime : Depends: php5 (>= 4.3.0) but it is not installed
                 Depends: php-pear (>= 1.6.0) but it is not installed
 php-mdb2 : Depends: php-pear but it is not installed
 php-net-dime : Depends: php-pear but it is not installed
 php-net-smtp : PreDepends: php-pear (>= 5.3.1-4) but it is not installed
 php-net-socket : Depends: php-pear but it is not installed
 php-net-url : Depends: php-pear but it is not installed
 php-soap : Depends: php-pear but it is not installed
 php5-memcache : Depends: php-pear (>= 1.4.0~b1) but it is not installed
 php5-memcached : Depends: php-pear (>= 1.4.0~b1) but it is not installed
 php5-ps : Depends: php5-gd but it is not installed
 python3 : Depends: python3.4 (>= 3.4.0-0~) but it is not installed
 python3-minimal : Depends: python3.4-minimal (>= 3.4.0-0~) but it is not instal
 software-properties-common : Depends: python3-software-properties (= 0.92.37.3)
 zlib1g:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
E: Unmet dependencies. Try using -f.
```

```
sudo apt-get update

Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/main Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/restricted Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/universe Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/multiverse Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/main amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/restricted amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/universe amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/multiverse amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/main i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/restricted i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/universe i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/multiverse i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/main Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/restricted Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/universe Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/multiverse Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/main amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/restricted amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/universe amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/main i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/restricted i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/universe i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/main Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/multiverse Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/restricted Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-updates/universe Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/main Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/restricted Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/universe Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/multiverse Sources
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/main amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/universe amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/main i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/restricted i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/universe i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/main Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/multiverse Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/restricted Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty-backports/universe Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/main Translation-en_US
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/main Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/multiverse Translation-en_US
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/multiverse Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/restricted Translation-en_US
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/restricted Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/universe Translation-en_US
  Unable to connect to sg.archive.ubuntu.com:http:
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) trusty/universe Translation-en
  Unable to connect to sg.archive.ubuntu.com:http:
Fetched 72 B in 5min 8s (0 B/s)
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en_US](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en_US)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en_US](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en_US)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en_US](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en_US)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en_US](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en_US)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/i18n/Translation-en](http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/i18n/Translation-en)  Unable to connect to sg.archive.ubuntu.com:http:


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

```
sudo apt-get upgrade

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libacl1:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libattr1:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libbz2-1.0:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libcap2:i386 : Depends: libc6:i386 (>= 2.8) but it is not installed
 libclass-dbi-mysql-perl : Depends: libdbd-mysql-perl but it is not installed
 libcomerr2:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libdb5.3:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libdbus-1-3:i386 : Depends: libc6:i386 (>= 2.10) but it is not installed
 libdrm2:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libjson-c2:i386 : Depends: libc6:i386 (>= 2.8) but it is not installed
 liblzma5:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libmysqlclient18 : Depends: mysql-common (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
 libtinfo5:i386 : Depends: libc6:i386 (>= 2.15) but it is not installed
 mysql-server-5.5 : Depends: mysql-client-5.5 (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
                    Depends: mysql-server-core-5.5 (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
                    PreDepends: mysql-common (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
 php-auth : Depends: php-pear (>= 1.4.0~b1) but it is not installed
            Recommends: php-file-passwd (>= 1.1.0) but it is not installable
            Recommends: php-net-pop3 (>= 1.3.0) but it is not installable
            Recommends: php-mdb but it is not installable
            Recommends: php-auth-radius but it is not installable
            Recommends: php-crypt-chap (>= 1.0.0) but it is not installable
            Recommends: php-file-smbpasswd (>= 1.0.0) but it is not installable
            Recommends: php-http-client (>= 1.1.0) but it is not installable
            Recommends: php-net-vpopmaild (>= 0.1.0) but it is not installable
            Recommends: php5-vpopmail (>= 0.2) but it is not installable
            Recommends: php5-kadm5 (>= 0.2.3) but it is not installable
            Recommends: php5-saprfc but it is not installable
 php-auth-sasl : Depends: php5 (>= 4.2.0) but it is not installed
                 Depends: php-pear (>= 1.4.3) but it is not installed
 php-db : Depends: php-pear but it is not installed
 php-gettext : Depends: php5 but it is not installed or
                        php5-cli but it is not installed
 php-http-request : PreDepends: php-pear (>= 5.3) but it is not installed
 php-log : Depends: php5 (>= 5.0.0) but it is not installed
           Depends: php-pear (>= 1.4.3) but it is not installed
           Recommends: php5-sqlite but it is not installed
 php-mail : Depends: php-pear (>= 1.5.6) but it is not installed
 php-mail-mime : Depends: php5 (>= 4.3.0) but it is not installed
                 Depends: php-pear (>= 1.6.0) but it is not installed
 php-mdb2 : Depends: php-pear but it is not installed
 php-net-dime : Depends: php-pear but it is not installed
 php-net-smtp : PreDepends: php-pear (>= 5.3.1-4) but it is not installed
 php-net-socket : Depends: php-pear but it is not installed
 php-net-url : Depends: php-pear but it is not installed
 php-soap : Depends: php-pear but it is not installed
 php5-memcache : Depends: php-pear (>= 1.4.0~b1) but it is not installed
 php5-memcached : Depends: php-pear (>= 1.4.0~b1) but it is not installed
 php5-ps : Depends: php5-gd but it is not installed
 python3 : Depends: python3.4 (>= 3.4.0-0~) but it is not installed
 python3-minimal : Depends: python3.4-minimal (>= 3.4.0-0~) but it is not installed
 software-properties-common : Depends: python3-software-properties (= 0.92.37.3) but 0.92.37.5 is installed
 zlib1g:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
E: Unmet dependencies. Try using -f.
```

```
sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libacl1:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libattr1:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libbz2-1.0:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libcap2:i386 : Depends: libc6:i386 (>= 2.8) but it is not installed
 libclass-dbi-mysql-perl : Depends: libdbd-mysql-perl but it is not installed
 libcomerr2:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libdb5.3:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libdbus-1-3:i386 : Depends: libc6:i386 (>= 2.10) but it is not installed
 libdrm2:i386 : Depends: libc6:i386 (>= 2.17) but it is not installed
 libjson-c2:i386 : Depends: libc6:i386 (>= 2.8) but it is not installed
 liblzma5:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
 libmysqlclient18 : Depends: mysql-common (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
 libtinfo5:i386 : Depends: libc6:i386 (>= 2.15) but it is not installed
 mysql-server-5.5 : Depends: mysql-client-5.5 (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
                    Depends: mysql-server-core-5.5 (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
                    PreDepends: mysql-common (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
 php-auth : Depends: php-pear (>= 1.4.0~b1) but it is not installed
            Recommends: php-file-passwd (>= 1.1.0) but it is not installable
            Recommends: php-net-pop3 (>= 1.3.0) but it is not installable
            Recommends: php-mdb but it is not installable
            Recommends: php-auth-radius but it is not installable
            Recommends: php-crypt-chap (>= 1.0.0) but it is not installable
            Recommends: php-file-smbpasswd (>= 1.0.0) but it is not installable
            Recommends: php-http-client (>= 1.1.0) but it is not installable
            Recommends: php-net-vpopmaild (>= 0.1.0) but it is not installable
            Recommends: php5-vpopmail (>= 0.2) but it is not installable
            Recommends: php5-kadm5 (>= 0.2.3) but it is not installable
            Recommends: php5-saprfc but it is not installable
 php-auth-sasl : Depends: php5 (>= 4.2.0) but it is not installed
                 Depends: php-pear (>= 1.4.3) but it is not installed
 php-db : Depends: php-pear but it is not installed
 php-gettext : Depends: php5 but it is not installed or
                        php5-cli but it is not installed
 php-http-request : PreDepends: php-pear (>= 5.3) but it is not installed
 php-log : Depends: php5 (>= 5.0.0) but it is not installed
           Depends: php-pear (>= 1.4.3) but it is not installed
           Recommends: php5-sqlite but it is not installed
 php-mail : Depends: php-pear (>= 1.5.6) but it is not installed
 php-mail-mime : Depends: php5 (>= 4.3.0) but it is not installed
                 Depends: php-pear (>= 1.6.0) but it is not installed
 php-mdb2 : Depends: php-pear but it is not installed
 php-net-dime : Depends: php-pear but it is not installed
 php-net-smtp : PreDepends: php-pear (>= 5.3.1-4) but it is not installed
 php-net-socket : Depends: php-pear but it is not installed
 php-net-url : Depends: php-pear but it is not installed
 php-soap : Depends: php-pear but it is not installed
 php5-memcache : Depends: php-pear (>= 1.4.0~b1) but it is not installed
 php5-memcached : Depends: php-pear (>= 1.4.0~b1) but it is not installed
 php5-ps : Depends: php5-gd but it is not installed
 python3 : Depends: python3.4 (>= 3.4.0-0~) but it is not installed
 python3-minimal : Depends: python3.4-minimal (>= 3.4.0-0~) but it is not installed
 software-properties-common : Depends: python3-software-properties (= 0.92.37.3) but 0.92.37.5 is installed
 zlib1g:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
E: Unmet dependencies. Try using -f.
```

---

### Post by Bucky Ball on 2015-09-25
[QUOTE=rudy7]I then attempted to install a package that failed ...[/QUOTE]

Would you mind telling us which? I presume you are online when you are trying to do the updating?

I'm presuming your install is a server install and you are specifically wanting to run a Ubuntu server here?

---

### Post by rudy7 on 2015-09-25
> **Bucky Ball said:**
> Would you mind telling us which? I presume you are online when you are trying to do the updating?

I'm presuming your install is a server install and you are specifically wanting to run a Ubuntu server here?

The package i attempted t install is called CentovaCast. ([http://www.centova.com/doc/cast/installation_manual/02_quick_installation](http://www.centova.com/doc/cast/installation_manual/02_quick_installation))

Yes it is the server version, and I am online.

To be honest, I wouldn't mind just formatting and re-installing, however the website I was working on is backed up on the machine (I hadn't downloaded it to an external drive just. yet), I am unable to connect via FTP or Webmin to save the backup. I don't know the file file name or the exact directory, else I would just take a copy and then re-install.

If at all possible I would like to salvage enough to retrieve that backup before re-installing if need be.

---

### Post by ian-weisser on 2015-09-25
> **rudy7 said:**
> ```
sudo apt-get autoremove
[...]
The following packages have unmet dependencies:
 libacl1:i386 : Depends: **libc6**:i386 (**>= 2.4**) but it is not installed
```

You seem to have introduced a version conflict. Your package manager won't work until you resolve it.

Here, take a look. These are the versions of libc6 in the Ubuntu repositories:
```
me@me:~$ rmadison libc6
 libc6 | 2.15-0ubuntu10    | precise          | amd64, armel, armhf, i386, powerpc
 libc6 | 2.15-0ubuntu10.11 | precise-security | amd64, armel, armhf, i386, powerpc
 libc6 | 2.15-0ubuntu10.12 | precise-updates  | amd64, armel, armhf, i386, powerpc
 libc6 | 2.19-0ubuntu6     | trusty           | amd64, arm64, armhf, i386, powerpc, ppc64el
 libc6 | 2.19-0ubuntu6.6   | trusty-security  | amd64, arm64, armhf, i386, powerpc, ppc64el
** libc6 | 2.19-0ubuntu6.6   | trusty-updates   | amd64, arm64, armhf, i386, powerpc, ppc64el**
 libc6 | 2.21-0ubuntu4     | vivid            | amd64, arm64, armhf, i386, powerpc, ppc64el
 libc6 | 2.21-0ubuntu4     | wily             | amd64, arm64, armhf, i386, powerpc, ppc64el

```
See the highest version for Trusty (14.04)? It's 2.19. Even Debian Sid currently only has 2.21.
Yet you have tried to install _something_ that wants version 2.4 or higher. And 2.4 (or higher) is simply not available in any of your current sources.

Completely uninstall your _something_. Delete it from your package cache. Purge it from your dpkg database.
Then ensure your package manager is properly working...so you will begin receiving security updates and bugfixes again.

That Centova link is not a package. Those are instructions to run some installer script. Totally different way to install software, usually unrelated to packages.
If it's an installer script that tries to install packages, then run away...down that path lies great frustration, and a fool of a developer.

---

### Post by rudy7 on 2015-09-25
> **ian-weisser said:**
> 

Completely uninstall your _something_. Delete it from your package cache. Purge it from your dpkg database.
Then ensure your package manager is properly working...so you will begin receiving security updates and bugfixes again.


Can you point me in the direction of instructions on how to do this?

---

### Post by rudy7 on 2015-09-25
I ran
```
sudo dpkg -p
``` for each of the unmet dependencies, and most were removed (I think). 

I then ran ```
sudo apt-get upgrade
```   and I get

```
sudo apt-get upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libmysqlclient18 : Depends: mysql-common (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
 mysql-server-5.5 : Depends: mysql-client-5.5 (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
                    Depends: mysql-server-core-5.5 (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
                    PreDepends: mysql-common (>= 5.5.44-0ubuntu0.14.04.1) but it is not installed
 php-http-request : PreDepends: php-pear (>= 5.3) but it is not installed
 php-net-dime : Depends: php-pear but it is not installed
 php-net-smtp : PreDepends: php-pear (>= 5.3.1-4) but it is not installed
                Recommends: php-auth-sasl but it is not installed
 php-net-socket : Depends: php-pear but it is not installed
 php-net-url : Depends: php-pear but it is not installed
 php-soap : Depends: php-pear but it is not installed
            Recommends: php-mail but it is not installed
            Recommends: php-mail-mime but it is not installed
 php5-memcache : Depends: php-pear (>= 1.4.0~b1) but it is not installed
 python3 : Depends: python3.4 (>= 3.4.0-0~) but it is not installed
 python3-minimal : Depends: python3.4-minimal (>= 3.4.0-0~) but it is not installed
 software-properties-common : Depends: python3-software-properties (= 0.92.37.3) but 0.92.37.5 is installed
 zlib1g:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
E: Unmet dependencies. Try using -f.

```

I then run 
```
apt-get -f install
```

and I get

```

Reading changelogs... Done
Preconfiguring packages ...
(Reading database ... 137519 files and directories currently installed.)
Removing cloud-init (0.7.5-0ubuntu1.10) ...
dpkg: error processing package cloud-init (--remove):
 cannot remove `/usr/lib/cloud-init/write-ssh-key-fingerprints': Permission denied
Removing postfix-mysql (2.11.0-1ubuntu1) ...
dpkg: error processing package postfix-mysql (--remove):
 cannot remove `/usr/lib/postfix/dict_mysql.so': Permission denied
Removing software-properties-common (0.92.37.3) ...
/var/lib/dpkg/info/software-properties-common.prerm: /usr/bin/py3clean: /usr/bin/python3: bad interpreter: No such file or directory
dpkg: error processing package software-properties-common (--remove):
 subprocess installed pre-removal script returned error exit status 126
/var/lib/dpkg/info/software-properties-common.postinst: /usr/bin/py3compile: /usr/bin/python3: bad interpreter: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 cloud-init
 postfix-mysql
 software-properties-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2015-09-25
> **rudy7 said:**
> ```

dpkg: error processing package cloud-init (--remove):
 cannot remove `**/usr/lib/cloud-init/write-ssh-key-fingerprints**': Permission denied
Removing postfix-mysql (2.11.0-1ubuntu1) ...
dpkg: error processing package postfix-mysql (--remove):
 cannot remove `**/usr/lib/postfix/dict_mysql.so**': Permission denied

```

Oh, dear.
Do you happen to know why the permissions or owner of those two files has been changed?
If not, you would be best advised to completely reinstall. Whatever you did to bork those permissions may (or may not) have caused other widespread damage. 

> **rudy7 said:**
> ```

Removing software-properties-common (0.92.37.3) ...
/var/lib/dpkg/info/software-properties-common.prerm: /usr/bin/py3clean: **/usr/bin/python3: bad interpreter: No such file or directory**
dpkg: error processing package software-properties-common (--remove):
 subprocess installed pre-removal script returned error exit status 126
/var/lib/dpkg/info/software-properties-common.postinst: /usr/bin/py3compile: **/usr/bin/python3: bad interpreter: No such file or directory**

```

Oh, dear.
You should reinstall the proper Ubuntu version of Python3 ASAP.

---

### Post by rudy7 on 2015-09-26
> **ian-weisser said:**
> Oh, dear.
Do you happen to know why the permissions or owner of those two files has been changed?
If not, you would be best advised to completely reinstall. Whatever you did to bork those permissions may (or may not) have caused other widespread damage. 



Oh, dear.
You should reinstall the proper Ubuntu version of Python3 ASAP.

I have no idea what was done that resulted in the changed permissions. That said, I managed to take a copy of the file system and now have a good back up of the website I was working on. I can format and re-install. This time I will take copious notes in order to avoid a similar situation.

Many thank to you and Bucky Ball for your help with this.

---

### Post by Bucky Ball on 2015-09-26
All good. Please mark this thread as solved and post a new one for any issues you have with the new install (unless, of course it is identical to this one, which is unlikely). See the first link in my signature, good luck and enjoy! :)

---

