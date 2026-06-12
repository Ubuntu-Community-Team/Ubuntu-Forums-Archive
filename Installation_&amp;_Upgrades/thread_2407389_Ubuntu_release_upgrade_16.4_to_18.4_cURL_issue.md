---
title: "Ubuntu release upgrade 16.4 to 18.4: cURL issue"
date: 2018-12-03
forum: Installation &amp; Upgrades
---

### Post by bnt.lz on 2018-12-03
Starting from a working environment I release upgraded from Ubuntu 16.4.5 LTE to 18.4.1 LTE.
Everithing went fine but following issue:

servece owncloud, claim php extension curl as not evailabe or installed.

I checked for that:
user@host: locate mods-available | grep -i curl
/etc/php/7.0/mods-available/curl.ini
/etc/php/7.2/mods-available/curl.ini
/var/lib/ucf/cache/:etc : php:7.0:mods-available:curl.ini
/var/lib/ucf/cache/:etc : php:7.2:mods-available:curl.ini

sudo phpenmod curl
sudo service apache2 restart

but problem was not solved.
Owncloud is a nice stong service for cloud sharing.

Any suggestion in order to better troubleshoot ?

---

