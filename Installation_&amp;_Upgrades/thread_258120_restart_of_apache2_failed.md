---
title: "restart of apache2 failed"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by fretn on 2006-09-15
hello,

I changed some virtualhosts in my apache2 config and when I tried to restart apache2 I received following error:

> 
sudo /etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)... Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load:
Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: undefined symbol: db_strerror_4002


any idea what's wrong ?

---

### Post by wavesound on 2007-03-11
HI
I get his after changing to php5.
I keep looking in Mods allowed and mods config.
I can see the config for PHP5.

Has Ubuntu moved the php5 module?


Cheers
Bob

---

### Post by antonmoura on 2007-04-30
Hello

  I had a similar problem. It was located in libdb4.1 of Berkeley DB. To solve the problem, I installed libdbd4.1 in a temporary directory and then overwrite the files in /usr/lib (libdb-4.1.a, libdb-4.1.la, etc). I also needed to install version 4.2 and overwrite the files in /usr/lib (libdb-4.2.a, libdb-4.2.la, etc) in the same way.

Bye.

---

