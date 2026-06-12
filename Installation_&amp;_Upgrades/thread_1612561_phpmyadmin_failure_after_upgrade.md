---
title: "phpmyadmin failure after upgrade"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by kinch on 2010-11-03
I'm quite frustrated right now, from everything I know about computing, ports, and phpmyadmin this should be working but I keep getting 2002 can't connect.

I want to access phpmyadmin on my local workstation after setting up a VPN tunnel vis-a-vis SSH ... I know the tunnel is working because the mysql command line tool works fine. 

eg: mysql -h127.0.0.1 -uuser -ppass

but I can't get phpmyadmin to connect no matter what I try

/etc/phpmyadmin/config-db.php has only two lines:
$dbserver='127.0.0.1';
$dbtype='mysql';

I know it isn't a browser thing because I can connect to a remote phpmyadmin without issue. 

anybody have any ideas?

---

### Post by efflandt on 2010-11-03
What webserver are you using for it?  For example if you are using apache2, you might need a symlink in /etc/apache2/sites-enabled pointing to /etc/phpmyadmin/apache.conf:

**sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/sites-enabled/.** (including trailing dot).  Then restart apache2.

But I do not know what protocol would give a 2002 error, because that does not sound like an http error.

---

### Post by Mike'sHardLinux on 2010-11-03
I believe 2002 is an error connecting to MySQL. Are you sure the webserver has connectivity to the MySQL server? Simply running the command mysql does not seem like a proper test in this situation.

Can you give a more detailed description of what you are doing? I am not understanding why you would use a VPN tunnel to connect to phpmyadmin when it is web-based.

---

