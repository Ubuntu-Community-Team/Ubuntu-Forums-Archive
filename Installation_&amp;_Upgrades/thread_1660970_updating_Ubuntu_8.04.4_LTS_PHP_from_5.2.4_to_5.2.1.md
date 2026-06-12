---
title: "updating Ubuntu 8.04.4 LTS PHP from 5.2.4 to 5.2.16"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by nickweavers on 2011-01-06
Hi,

I have a web server with Ubuntu 8.04.4 LTS installed on it and it is currently running php 5.2.4
```
apt-show-versions | grep php
php5-cli/hardy uptodate 5.2.4-2ubuntu5.12
php5-imap/hardy uptodate 5.2.3-0ubuntu3.1
psa-php5-configurator/hardy uptodate 1.5.3-ubuntu8.04.build95100504.17
php5-tidy/hardy uptodate 5.2.4-2ubuntu5.12
libapache2-mod-php5/hardy uptodate 5.2.4-2ubuntu5.12
php5-curl/hardy uptodate 5.2.4-2ubuntu5.12
php5-mcrypt/hardy uptodate 5.2.3-0ubuntu1
php5-xsl/hardy uptodate 5.2.4-2ubuntu5.12
php5-common/hardy uptodate 5.2.4-2ubuntu5.12
php5-cgi/hardy uptodate 5.2.4-2ubuntu5.12
php5-dev/hardy uptodate 5.2.4-2ubuntu5.12
php5-mysql/hardy uptodate 5.2.4-2ubuntu5.12
php-pear/hardy upgradeable from 5.2.4-2ubuntu5.10 to 5.2.4-2ubuntu5.12
php5-gd/hardy uptodate 5.2.4-2ubuntu5.12
php5-pspell/hardy uptodate 5.2.4-2ubuntu5.12

```
I am trying to write a php application that uses the DateTime class but the version in 5.2.4 is missing a number of useful methods (such as DateTime::diff, DateTime::add, DateTime::sub).
I would like to get the php version updated to 5.2.16 which does have these. Is this possible using apt-get.

Also, I can see that apt-get has a --simulate flag, so does using this make it completely safe just to try a command and observe what it would do?

I'm not a Linux expert, but I know my way around from a few years of using it. This is a live server, though, so I need to be careful. (It is regularly backed up, but I don't want to end up having to find out how good the backups are if I can help it ;0) )   

TIA,
Nick

---

