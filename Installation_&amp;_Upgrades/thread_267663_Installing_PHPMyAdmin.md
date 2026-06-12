---
title: "Installing PHPMyAdmin"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-09-28
when I tried installing PHPMyAdmin on my Ubuntu 6.06 Desktop, I always got this error:

```

sudo apt-get install phpmyadmin
Reading package lists ... Done
Building dependencies ... Done
E:Couldn't find package phpmyadmin

```

What I already did is I ran these lines

sudo apt-get update
sudo apt-get upgrade

Hope you could help us on this.

---

### Post by neptune39 on 2006-09-28
Have you added the other repositries, not sure if phpmyadmin is in them or not but seems the most obvious first thing to me.

---

### Post by jordantbro on 2006-09-28
Hasn't anyone put together a guide for adding phpmyadmin to Ubuntu server?  I would really appreciate one.

---

### Post by textguru on 2006-09-29
I already got the installation

I just follow the instruction on [http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_for_Apache_HTTP_Server)

What I did is I've changed the repositories. I've uncommented the lines with 

dapper-backports main restricted universe multiverse

and run apt-get update

and it works.

---

### Post by binbash on 2006-09-29
just download phpmyadmin and extract it (you can extract it anywhere yo want in public_Html) thats all.

---

### Post by adamosis on 2006-10-25
Installed phpmyadmin as instructed via [http://ubuntuguide.org/wiki/Dapper#H...he_HTTP_Server](http://ubuntuguide.org/wiki/Dapper#H...he_HTTP_Server)

However, now receiving the following line in apache error log:

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/msql.so' - /usr/lib/php5/20051025/msql.so: cannot open shared object file: No such file or directory in Unknown on line 0

This is a result of uncommenting 'extension=mysql.so' in php.ini. Should I recomment this? I also don't have a phpmyadmin folder in www? Any thoughts on this?

Thanks!

---

