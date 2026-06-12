---
title: "Installed PHP 8.2 but it did not read changed php.ini"
date: 2024-01-20
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2024-01-20
Firstly it would be nice when I install a new release of PHP if I did not have to reenter **all** of my changes to php.ini.  The rest of this note is just to document some of the hoops I had to go through to get this to work.  This is partly because I was not using PHP-FPM with 8.1, it may not have been an option when I installed 8.1 two years ago, but the 8.2 install defaulted to it.

/etc/php/8.2/fpm/php.ini includes the following modified lines
...
; How many GET/POST/COOKIE input variables may be accepted
max_input_vars = 5000
...
; UNIX: "/path1:/path2"
include_path = ".:/usr/share/php:/home/jcobban/include

sudo apache2ctl restart

No change to phpinfo output.  This is different from the behaviour under PHP without FPM.

I am migrating from PHP 8.1 which is in its last year of support to PHP 8.2.  phpinfo informs me that it read /etc/php/8.2/fpm/php.ini but even though I changed /etc/php/8.2/fpm/php.ini to include the options that I have overridden in every release for the past 20 years, and restarted the Apache2 server, those changes did not show up, and my local website did not work as a consequence. I restarted Apache2, which is all that I had to do previously, but that did not change.  I have now read some of the documentation of PHP-FPM but I still do not understand this difference in behaviour.

$ sudo service php-fpm restart
Failed to restart php-fpm.service: Unit php-fpm.service not found.
$sudo systemctl restart php8.2-fpm
[no response]
**Now** phpinfo shows that it has read the changes to php.ini.

I couldn't find a statement on any of the Ubuntu web sites specifying exactly what command should be issued to restart php-fpm, or explaining why a separate restart is required.  The lack of any response to systemctl restart is slightly unnerving.  Why should I have to issue **another** command to see that the server has actually restarted.  This is only for the testing website on my development computer, which is only accessible from my development computer, and I am running Apache2, not NGINX, so I was not expecting this unfamiliar service to suddenly appear on my development system.

---

