---
title: "LAMP PHP not working ( Trusty Server )"
date: 2014-10-25
forum: Installation &amp; Upgrades
---

### Post by Xriva on 2014-10-25
I have installed Trusty Server ( and loaded LAMP during the install.)
MySQL and Apache test ok

But the PHPINFO test file doesn't load into the FireFox browser   - Here are the directions I followed : [www.htmlgoodies.com/beyond/php/article.php/3472431](www.htmlgoodies.com/beyond/php/article.php/3472431)

FireFox popup identifies the file as a PHP scripts and asks if I want to open it in the browser - clicking OK just returns the same popup.
    -  located in the /var/www directory.
    -  I've also run chmod 777 on this file.

However PHP is running - because I can use it from the command line - for example :

              echo "<?php phpinfo(); ?>" | php

Works

 . . . .  so I probably have something misconfigured.

Ideas ?

Kevin / Xriva

---

### Post by Doug S on 2014-10-25
Did you change your DocumentRoot from /var/www/html to /var/www? By default on 14.04, the file would be expected to be found in /var/www/html. Otherwise it should work by default, but please review [the Ubuntu Serverguide]("https://help.ubuntu.com/14.04/serverguide/php5.html#php5-configuration") .

---

### Post by Xriva on 2014-10-25
Doug,

Thank you for your help - that fixed it !

Hopefully this info will help the next Newbie.


I did a lot of reading - but must have missed that detail in the volumne.

Kevin / Xriva

---

### Post by Xriva on 2014-10-26
While it is self depreciating, I wanted to add info that might help the next person.

When I tested Apache using 127.0.0.1 the result included info concerning Document Root.

"
Document Roots

By default, Ubuntu does not allow access through the web browser to any file apart of those located in /var/www, public_html directories (when enabled) and /usr/share (for web applications). If your site is using a web document root located elsewhere (such as in /srv) you may need to whitelist your document root directory in /etc/apache2/apache2.conf.

The default Ubuntu document root is /var/www/html. You can make your own virtual hosts under /var/www. This is different to previous releases which provides better security out of t
"

Had I actually READ that I would've known where to place the PHP test file.

Note - most of the web sites describing the PHP Test are a bit dated and refer to the old / traditional Document Root location.

Lesson learned : Should PHP fail, check the Apache Document Root setting.

HTH, 
  Kevin / Xriva

---

