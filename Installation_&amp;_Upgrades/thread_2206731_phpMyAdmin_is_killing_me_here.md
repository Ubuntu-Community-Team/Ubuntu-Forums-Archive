---
title: "phpMyAdmin is killing me here"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by jeff41 on 2014-02-20
Running 12.04
I loaded phpMyAdmin with the apt-get and thought I did everything right (I know they always think that).

I am getting the following in my browser trying to connect: 

Not Found
The requested URL /phpMyAdmin was not found on this server.
Apache/2.2.22 (Ubuntu) Server at 192.168.1.205 Port 80

I found help at [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin) and followed those instructions to plow it and reconfigure.

After doing the reload, I get this:
[Thu Feb 20 09:31:43 2014] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Line 3 in /etc/phpmyadmin/apache.conf reads: Alias /phpmyadmin /usr/share/phpmyadmin

I cannot figure out where the 127.0.1.1 is coming from.  

Jeff

---

