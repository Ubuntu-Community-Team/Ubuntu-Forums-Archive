---
title: "Mcrypt not working in the latest ubuntu version 14.04 nginx php5-fpm. Please help."
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by Vinodh_Kumar on 2014-12-08
[COLOR=#333333][FONT=monospace]Dear Team,

I have tried all the things available in the internet but I am not able to fix this. Please help.

I have done the following:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]sudo apt-get install mcrypt
sudo apt-get install php5-mcrypt
sudo ln -s /etc/php5/fpm/conf.d/20-mcrypt.ini /etc/php5/mods-available/mcrypt.ini
sudo php5enmod mcrypt[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I then have restarted php-fpm (and actually restarted nginx as well, just in case)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]When i go to the page with the mcrypt functions i get the following in the log:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]2014/12/08 15:12:24 [error] 10779#0: *3 FastCGI sent in stderr: "PHP message: PHP Fatal error: Call to undefined function mcrypt_module_open() in /mnt/persistent1/mcrypttest/mcrypttesting.php on line 5" while reading upstream, client: 127.0.0.1, server: localhost, request: "GET /dbtest/a.php HTTP/1.1", upstream: "fastcgi://unix:/var/run/php5-fpm.sock:", host: "localhost"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]phpinfo shows the authors of mcrypt, but that's the only entry[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Also:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]$ php5-fpm -m|grep mcrypt
mcrypt[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]$ sudo apt-cache policy php5-mcrypt
php5-mcrypt:
  Installed: 5.4.6-0ubuntu5
  Candidate: 5.4.6-0ubuntu5
  Version table:
 *** 5.4.6-0ubuntu5 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
        100 /var/lib/dpkg/status[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]So it's there, but just doesn't do anything.

Thank you[/FONT][/COLOR]

---

### Post by sandyd on 2014-12-08
You have the ln commands incorrect, the propper syntax is
```
ln -s [target] /path/to/create/link/at
```

The target is what you are linking to.

In this case, it would be
```

sudo ln -s /etc/php5/mods-available/mcrypt.ini /etc/php5/fpm/conf.d/20-mcrypt.ini
```

---

### Post by Vinodh_Kumar on 2014-12-09
I have done that too but it is still not working. Please help

My Linux Version is 14.04 running nginx with php5-fpm

---

### Post by sandyd on 2014-12-10
> **Vinodh_Kumar said:**
> I have done that too but it is still not working. Please help

My Linux Version is 14.04 running nginx with php5-fpm

Whats the output of```

ls -l /etc/php5/fpm/conf.d/
ls -l /etc/php5/mods-available/
```
Could be that there is a dangling symlink around

---

