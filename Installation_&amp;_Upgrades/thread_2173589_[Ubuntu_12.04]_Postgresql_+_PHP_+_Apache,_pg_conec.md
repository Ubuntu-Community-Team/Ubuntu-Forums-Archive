---
title: "[Ubuntu 12.04] Postgresql + PHP + Apache, pg_conect() undefined"
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by sopel1000 on 2013-09-10
Hi, I am really stuck. I have installed:

```
Apache/2.5.0-dev (Unix) OpenSSL/1.0.1 PHP/5.4.9-dev 
```

(Yes, I have to have exactly these versions of Apache and PHP)

Problem:

```
Fatal error: Call to undefined function pg_connect()
```

I have installed **php5-pgsql **as well as **postgresql **and **postgresql-client**. I need postgresql, but I can't use it... I thought there was a problem with LibPQ, so I tried to force it by putting "LoadModule PATH/libpq.so" but Apache says that the module has already been loaded.

If I try to uncomment "extension=php_pgsql.dll" in php.ini it shows that the file does not exist (the same happens for php_pdo_pgsql file) and when I tried to find it, the find command only showed me that "php_pgsql.h" exists.

Could you please help me? I am out of ideas.

---

### Post by SeijiSensei on 2013-09-10
Create a file called something like "info.php" in /var/www with just the contents:
```
<?php phpinfo() ?>
```

Now browse to that file; you wlll see a complete list of all the modules running in PHP.  Are the pgsql modules installed?

---

### Post by sopel1000 on 2013-09-10
Of course I did that, that was the first thing I did. No, pgsql modules are **not **loaded, surprisingly **sqlite** PDO modules are loaded, but neither have I installed them nor have I enabled this extension.

I am sure which php.ini I am editing because phpinfo says:

> Loaded Configuration File 	/usr/local/apache2/conf/php.ini 

---

### Post by sopel1000 on 2013-09-11
Hi, does anyone have any clue or has faced the same problem?

---

### Post by sopel1000 on 2013-09-12
Of course even if I put extension=php_pgsql.so, it doesn't help.

---

### Post by sopel1000 on 2013-09-16
Thanks **SeijiSensei **for writing anything and generally thank you everyone for no help at all. I got used to it on this forum.

For the record, I have not resolved this particular issue. There is one thing however - pgsql is not included when php is ran by webserver. If I run it from CLI and check php -i.... the php_pdo_pgsql and php_pgsql are both loaded!

**If you happen to know how to make it work, please, be so kind and reply.** Any kind of input is priceless.

---

### Post by sopel1000 on 2013-09-21
Solution: just recompile Apache and PHP.

---

