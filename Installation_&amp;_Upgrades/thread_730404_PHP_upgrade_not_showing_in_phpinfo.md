---
title: "PHP upgrade not showing in phpinfo"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by its_joy on 2008-03-20
Hello,

I am trying to upgrade to php 5.2.5, i downloaded the php tar file and configured it like this

./configure --prefix=/usr --enable-cgi --with-pear --with-openssl --with-zlib --with-bz2 --enable-ftp --with-gd --with-kerberos --with-mysql --with-mysqli --disable-posix --with-pgsql --enable-force-cgi-redirect --enable-calendar --with-imap --with-imap-ssl --with-curl --with-mcrypt --enable-embedded-mysqli./configure --prefix=/usr/bin --enable-cgi --with-pear --with-openssl --with-zlib --with-bz2 --enable-ftp --with-gd --with-kerberos --with-mysql --with-mysqli --disable-posix --with-pgsql --enable-force-cgi-redirect --enable-calendar --with-imap --with-imap-ssl --with-curl --with-mcrypt --enable-embedded-mysqli

Then i copied the recommended php.ini file to /etc/php5/apache2/php.ini
Finally i restarted apache, then run phpinfo() but i am still getting version 5.1.2

So I would like help on this: some guidance

Waiting for answer from you.

---

### Post by whazooo on 2008-03-21
I assume you had php installed from synaptic or a dist deb.
I also assume you are running gutsy.

If so, your gonna have trouble upgrading with a tar. and is not recommended.

Have a look at this post.

[http://ubuntuforums.org/showthread.php?t=701574](http://ubuntuforums.org/showthread.php?t=701574)

Also search for backporting php5.2.5 to gutsy

---

