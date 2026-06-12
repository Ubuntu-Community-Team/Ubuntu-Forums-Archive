---
title: "Trouble with phpmyadmin after 20.04 upgrade"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by townhill on 2020-04-26
I upgraded from 19.10 to 20.04 and everything is working well except for the Apache webserver and phpmyadmin.  After the upgrade the server would not start.  i removed and reinstalled Apache2 and it is running now but it would not connect to phpmyadmin.  i removed, purged and reinstalled phpmyadmin and now an unformatted page comes up on phpmyadmin that just shows php code, not the user interface.  Can anyone offer suggestions for fixing this? Not sure if this is an issue with the apache configuration   I have php version 3.4.0.  i am running a mariadb server which seems to be fine, can see my databases, etc.  Also, .php webpages in my var/www/html folder are not connecting to the database but just show the php code.   Thanks

---

### Post by SeijiSensei on 2020-04-26
You probably need to install the package libapache2-mod-php.  It contains the code that invokes PHP when .php and similar extensions are encountered.

This problem is avoided if you install the LAMP package:
```
sudo apt install lamp-server^
```
but you'll get MySQL rather than MariaDB.  The LAMP package installs all the interstitial packages like libapache2-mod-php automatically.

---

### Post by townhill on 2020-04-26
Thanks for the reply.  I checked and i already have libapache2-mod-php version (2:7.4+75) installed.  i have both php 7.3 and 7.4 installed, not sure which one is being used but 7.64 was there after the upgrade.
I don't know if installing LAMP might fix the problem but i would give it a try.  Should I remove the current Apache2 and phpmyadmin installations before installing it?

---

### Post by townhill on 2020-04-26
So it seems the problem is that apache will not parse a php file.  i created a phpinfo file and my browser just asks me if I want to download it, does not interpret it as php.  It must be a problem in my apache config so I'm poking around htere.

---

### Post by townhill on 2020-04-27
In the end. I uninstalled Apache, phpmyadmin *and* php.  Reinstalled it all this morning and all is working.   i did have two versions of php installed, 7.3 and 7.4.  I noticed that Apache was looking to load lib.php7.3.so which i didnt see in the php folder but i reinstalled just 7.4. I also noticed that the localhost IP address is now changed from 192.168 to 127.0.0.1.  My php pages would still load with the old ip address but php did not run.  When I updated the links with the 127.0.0.1  address it worked fine.

---

