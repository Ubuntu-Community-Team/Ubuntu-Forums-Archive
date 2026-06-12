---
title: "Lucid Upgrade killed my PHP scripts"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by nullmind on 2010-05-06
I had a simple LAMP development server on this machine for local web development from my public_html/ inside my home directory. I was using the following:

[LIST]
[*]Apache2
[*]PHP5
[*]Apache userdir module
[*]Apache php5 module
[*]MySQL5
[/LIST]

When I did the upgrade to Lucid, my PHP scripts stopped being parsed. All I can ever get is this source, so Apache doesn't seem to have the AddType for PHP, but I've manually added and restarted the server to do this. I've also removed the packages in question entirely (with config in Synaptic) and re-installed them without luck.

PHP is working though, because phpmyadmin works. Here is the permissions of my home, public_html directories, and a PHP script:

```

drwxr-xr-x 65 kris kris 4096 2010-05-06 09:24 kris

drwxr-xr-x 17 kris www-data      4096 2010-05-05 18:09 public_html

-rw-r--r--  1 kris www-data  2052 2009-11-04 09:44 index.php

```

Any ideas?

---

### Post by nullmind on 2010-05-06
```
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
    #<IfModule mod_userdir.c>
    #    <Directory /home/*/public_html>
    #        php_admin_value engine Off
    #    </Directory>
    #</IfModule>
</IfModule>

```

---

