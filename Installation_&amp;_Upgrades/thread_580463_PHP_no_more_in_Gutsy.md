---
title: "PHP no more in Gutsy?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Stex on 2007-10-18
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server

Most PHP files are being served for download rather than being executed on my new Gutsy desktop (a desktop install, I install apache etc. to test my work). A few php files do get executed and work but most (including [COLOR="Navy"]<?php phpinfo(); ?>[/COLOR]) are served for download.

libapache2-mod-php5 was installed fine, I even tried reinstalling it. /etc/apache2/mods-available/php5.conf is: (I haven't edited it, all my php files end in .php)
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

I don't get it, I've installed apache, php & mysql many times on ubuntu without hassle but now it doesn't want to play nice.

---

### Post by disasm on 2007-10-19
make sure symlinks exist for php5.conf and php5.load in /etc/apache2/mods-enabled.

Sam

---

### Post by adza on 2007-10-24
hi disasm, i have these same issues, have got the symlinks in that directory however..

> lrwxrwxrwx 1 root root 27 2007-10-24 18:37 php5.load -> ../mods-available/php5.load
lrwxrwxrwx 1 root root 27 2007-10-24 18:37 php5.conf -> ../mods-available/php5.conf


are these correct?

---

### Post by Stex on 2007-10-27
Hey adza, sorry I wasn't watching this. I had symlinks fine too, yours are correct also. I was able to fix this problem with the most unusual of methods - restarting ubuntu. I tried restarting Apache and all that but only the full reboot made everything work fine.

I don't know what caused this bug but at least it fixed itself overnight for me :lolflag:

---

