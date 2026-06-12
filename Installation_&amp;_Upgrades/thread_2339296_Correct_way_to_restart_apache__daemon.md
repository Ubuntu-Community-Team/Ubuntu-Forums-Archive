---
title: "Correct way to restart apache  daemon"
date: 2016-10-07
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2016-10-07
Environment: Ubuntu 16.04

It appears there are multiple ways to restart apache2

$ sudo /etc/init.d/apache2 restart

$ [COLOR=#3A3A3A][FONT=monospace]sudo systemctl restart apache2

$ sudo service apache2 restart

They all seem to work. However, I am wondering if there is a recommended way to restart apache2 (or any other daemon I guess).

Thank you in advance for your help.

Regards,
Peter
 
[/FONT][/COLOR]

---

### Post by sisco311 on 2016-10-07
All three commands will do the same thing. Ubuntu 16.04 defaults to systemd, so systemctl is the appropriate command to control it.  The other two commands are available for backward compatibility with the old init systems used by earlier versions of Ubuntu, namely Upstart and SystemV init.

---

