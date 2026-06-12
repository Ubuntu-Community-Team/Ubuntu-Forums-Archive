---
title: "PHP 7.4 FastCGI Process Manager - Failed"
date: 2020-06-13
forum: Installation &amp; Upgrades
---

### Post by hikeventures on 2020-06-13
Does anyone know how I can fix these errors?

&#9679; php7.4-fpm.service - The PHP 7.4 FastCGI Process Manager
   Loaded: loaded (/lib/systemd/system/php7.4-fpm.service; enabled; vendor prese
   Active: failed (Result: exit-code) since Sat 2020-06-13 17:07:23 CEST; 23s ag
     Docs: man:php-fpm7.4(8)
  Process: 27346 ExecStopPost=/usr/lib/php/php-fpm-socket-helper remove /run/php
  Process: 27331 ExecStart=/usr/sbin/php-fpm7.4 --nodaemonize --fpm-config /etc/
 Main PID: 27331 (code=exited, status=78)
lines 1-8/8 (END)
Unit service.service could not be found.
&#9679; php7.4-fpm.service - The PHP 7.4 FastCGI Process Manager
   Loaded: loaded (/lib/systemd/system/php7.4-fpm.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2020-06-13 17:07:23 CEST; 23s ago
     Docs: man:php-fpm7.4(8)
  Process: 27346 ExecStopPost=/usr/lib/php/php-fpm-socket-helper remove /run/php/php-fpm.sock /etc/php/7.4/
  Process: 27331 ExecStart=/usr/sbin/php-fpm7.4 --nodaemonize --fpm-config /etc/php/7.4/fpm/php-fpm.conf (c
 Main PID: 27331 (code=exited, status=78)

---

### Post by SeijiSensei on 2020-06-13
I installed the LAMP server package to get a fresh installation of PHP 7.4 running under Apache 2.  If I try to install php7.4-fpm, I get this warning from apt:

```

NOTICE: Not enabling PHP 7.4 FPM by default.
NOTICE: To enable PHP 7.4 FPM in Apache2 do:
NOTICE: a2enmod proxy_fcgi setenvif
NOTICE: a2enconf php7.4-fpm
NOTICE: You are seeing this message because you have apache2 package installed.

```
Did you do these things? Still not working? What are you trying to accomplish? Replace the PHP module in Apache with FastCGI, or use FastCGI from the command prompt?

---

