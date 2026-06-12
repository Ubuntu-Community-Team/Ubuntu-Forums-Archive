---
title: "PHP 5.3 and Lucid"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by shoaibnawaz on 2010-05-10
I installed lucid beta last month on my laptop and had been continuously updating it. As a php developer I had been developing website using drupal CMS and there was not any issue. I waited for a week after the Ubuntu is released.
Now I updated my office machine from Karmic to Lucid and after that I have lost the working php workstation. Now each php script is downloaded instead being parsed by php engine.
I checked for loaded modules in Apache using the command;

$ apache2ctl -M

and found
    php5_module (shared)

I also checked for "/etc/apache2/mods-available/php.conf"

<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
        SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>

and "/etc/apache2/mods-available/php.load" as

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so


$ php -v

PHP 5.3.2-1ubuntu4 with Suhosin-Patch (cli) (built: Apr  9 2010 08:18:14) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies
    with Xdebug v2.0.5, Copyright (c) 2002-2008, by Derick Rethans
    with Suhosin v0.9.29, Copyright (c) 2007, by SektionEins GmbH

How to get out of this situation?

---

### Post by Smiecho on 2010-05-17
If you have your PHP code in your home/public_html directory then:
> # To re-enable php in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.

It happened to me as well. And I also haven't read those line... :)

---

