---
title: "Upgrade in php broke websites with deprecated errors"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by DantePasquale on 2011-02-09
Hi,

I'm running:

```
PHP Version 5.3.2-1ubuntu4.7

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
Linux cocoanet.us 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux

Server version: Apache/2.2.14 (Ubuntu)
Server built:   Nov 18 2010 21:19:09
Server's Module Magic Number: 20051115:23
Server loaded:  APR 1.3.8, APR-Util 1.3.9
Compiled using: APR 1.3.8, APR-Util 1.3.9
Architecture:   64-bit
Server MPM:     Prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APACHE_MPM_DIR="server/mpm/prefork"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=128
 -D HTTPD_ROOT=""
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_LOCKFILE="/var/run/apache2/accept.lock"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="/etc/apache2/mime.types"
 -D SERVER_CONFIG_FILE="/etc/apache2/apache2.conf"

```

After recent upgrade in PHP, many applications have quit working (jinzora2 & 3, gallery2). There errors I'm seeing look more like warnings, but they applications do appear broken.

For gallery2 here's what I see:

```
Deprecated: Assigning the return value of new by reference is deprecated in /var/www/web1/web/dantepasquale/gallery2/bootstrap.inc on line 43
```

For jinzora3:

An entire page of similar warnings:

```
Deprecated: Assigning the return value of new by reference is deprecated in /var/www/web1/web/dantepasquale/jinzora3/frontend/frontends/slick/blocks.php on line 1562

Deprecated: Assigning the return value of new by reference is deprecated in /var/www/web1/web/dantepasquale/jinzora3/frontend/frontends/slick/blocks.php on line 1662
```

Both Gallery2 and Jinzora forums say to change the php.ini setting for error_reporting to:

error_reporting = E_ALL & ~E_NOTICE

But that's what I already had in all my php.ini files :(

Other posts suggest downgrading PHP but I really don't want to do that. So other than trying to fix the code in Jinzora3 and Gallery2 does anyone have any other suggestions?

Thanks, Danté

---

