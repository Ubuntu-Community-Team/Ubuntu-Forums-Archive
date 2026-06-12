---
title: "php commented out from /etc/mime.types"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by belgarth on 2012-10-19
Hi everyone,

I ran into a problem after upgrading to 12.04 to 12.10 where apache would no longer intepret [http://hostname/page](http://hostname/page) as the file page.php. After several hours of troubleshooting I found the issue to be due to that the following lines inside of /etc/mime.types had been commended out:

application/x-httpd-eruby                       rhtml
application/x-httpd-php                 phtml pht php
application/x-httpd-php-source                  phps
application/x-httpd-php3                        php3
application/x-httpd-php3-preprocessed           php3p
application/x-httpd-php4                        php4
application/x-httpd-php5                        php5

I haven't been able to find anyone else mentioning this problem. Anyone have any ideas why these lines are commented out after the upgrade?

---

### Post by Doug S on 2012-10-19
Is it specifically taken care of in /etc/apache2/mods-available/php5.conf now?
I notice differences in that file between 12.04 and 12.10 related to file name (extention).

---

### Post by belgarth on 2012-10-19
The releavant part of php5.conf is:

    <FilesMatch ".+\.ph(p[345]?|t|tml)$">
        SetHandler application/x-httpd-php

The regex expression is slightly modified between 12.04 and 12.10, but it seems to be irrelevant (switching it back to the original expression did not change). It seems like the fact that the mime.types has the pairing between php file types and x-httpd-php removed prevents the SetHandler from actually working.

---

### Post by Doug S on 2012-10-19
I get the same as you. I tried it on a brand new 12.04 server installation and a new 12.10 server. The 12.04 loaded the file with the .php extention and the 12.10 said it couldn't find the file.

---

