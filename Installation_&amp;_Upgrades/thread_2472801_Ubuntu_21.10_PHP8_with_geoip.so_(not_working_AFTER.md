---
title: "Ubuntu 21.10 PHP8 with geoip.so (not working AFTER upgrade)"
date: 2022-03-13
forum: Installation &amp; Upgrades
---

### Post by matthys on 2022-03-13
I did a upgrade from 21.04 (PHP7.4) to 21.10 with PHP8 etc.

Before I always could use the php function **geoip_country_code_by_name** as mention in the php manual:
[https://www.php.net/manual/en/function.geoip-country-code-by-name.php](https://www.php.net/manual/en/function.geoip-country-code-by-name.php)

But now it seems it's not working and if I test I get:
PHP Warning:  PHP Startup: Unable to load dynamic library 'geoip.so' (tried: /usr/lib/php/20200930/geoip.so (/usr/lib/php/20200930/geoip.so: cannot open shared object file: No such file or directory), /usr/lib/php/20200930/geoip.so.so (/usr/lib/php/20200930/geoip.so.so: cannot open shared object file: No such file or directory)) in Unknown on line 0

It seems it's looking in wrong directory as I do find it at /usr/lib/php/20160303/geoip.so

I also check PHP and module is there:
/etc/php/8.0/mods-available/geoip.ini, which contains the line: extension=geoip.so

So, what is going on and how do I fix this?

Hmmmm ... could this be the problem?

File list of package php-geoip in focal of architecture amd64
/etc/php/7.4/mods-available/geoip.ini
**/usr/lib/php/20190902/geoip.so**
/usr/share/doc/php-geoip/README
/usr/share/doc/php-geoip/changelog.Debian.gz
/usr/share/doc/php-geoip/copyright

File list of package php-geoip in impish of architecture amd64
/etc/php/8.0/mods-available/geoip.ini
/usr/share/doc/php-geoip/README
/usr/share/doc/php-geoip/changelog.Debian.gz
/usr/share/doc/php-geoip/copyright

No geoip.so ???

---

### Post by matthys on 2022-03-13
It seems that /usr/lib/php/20160303/geoip.so is a very old one .... probably not cleaned-up

---

### Post by matthys on 2022-03-14
Got a reply from question to package maintainers and they said:

I found a remark that php-geoip works only with php versions 5 and 7, but impish has version 8. In jammy that package does not exist at all.

However strange to get a broke packaged in the first place ....

There is also a bug report on Debian -> [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1003555](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1003555)
php-geoip doesn't support PHP 8 **and** depends on already deprecated geoip library (replaced by libmmdb).

---

