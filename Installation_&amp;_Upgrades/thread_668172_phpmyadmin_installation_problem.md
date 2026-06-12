---
title: "phpmyadmin installation problem"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by honiball on 2008-01-15
I have installed phpMyAdmin on my Ubuntu 6.06.  Everything seemed to go OK until I tried to access the website.  I go the following errors along with the expected website:


Warning: preg_match: internal pcre_fullinfo() error -3 in /usr/local/apache2/htdocs/phpMyAdmin-2.11.4-english/libraries/core.lib.php on line 356

Warning: Cannot modify header information - headers already sent by (output started at /usr/local/apache2/htdocs/phpMyAdmin-2.11.4-english/libraries/core.lib.php:356) in /usr/local/apache2/htdocs/phpMyAdmin-2.11.4-english/libraries/auth/cookie.auth.lib.php on line 109


Below that I also got the following:
Error:
The configuration file now needs a secret passphrase (blowfish_secret).

The file I downloaded and installed is: phpMyAdmin-2.11.4-english.tar.gz
My Apache2 webserver is serving files from: /usr/local/apache2/htdocs
I installed phpmyadmin to that location.

Any ideas?

Thanks.

Andrew

---

### Post by jd65pl on 2008-01-15
phpmyadmin should be available from the repos, have you tried that version?

---

### Post by honiball on 2008-01-17
I have tried it using:           sudo apt-get install phpmyadmin

I couldn't even get it to launch the website after that.  I am not sure if my Apache2 is serving from the proper location.  My websites are being served from
/usr/local/apache2/htdocs

Anyway, I installed it from source, and managed to get it to work.  I have also managed to solve the problem in this posting by editing the php.ini file as follows:
error_reporting = E_ERROR

Aparently this will only display critical errors.

Thanks.

Andrew

---

