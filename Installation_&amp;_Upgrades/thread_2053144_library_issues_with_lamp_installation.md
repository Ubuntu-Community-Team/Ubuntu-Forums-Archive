---
title: "library issues with lamp installation"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by ixxalnxxi on 2012-09-04
i'm using

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise


it's 64 bit. after the lamp installation, i noticed some libraries were missing: 

php: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory


after some googling i was told it was a library mismatch issue since it's expecting 32 bit libs but i have 64 bit, so i made several symlinks for the missing package but things ended up not working:

php: /usr/lib/x86_64-linux-gnu/libmysqlclient.so.15: no version information available (required by php)
php: Symbol `client_errors' has different size in shared object, consider re-linking
php: symbol lookup error: php: undefined symbol: utf8_countTrailBytes_3_6


how would i restore my lib files to their original state and install pear/php to be 64 bit compatible?

---

