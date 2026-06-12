---
title: "Unable to change the MySQL datadir"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by rahbz on 2013-06-13
As given in the below forum thread, I followed all the steps[URL="http://lists.mysql.com/mysql/220448"]
http://lists.mysql.com/mysql/220448[/URL]
But after changing the datadir option in my.conf, MySQL will not get started showing this 
ganit@garo:~$ sudo service mysql start
start: Job failed to start

Even if I just change the name of /var/lib/mysql to /var/lib/mysql_old
and change name accordingly in my.conf, service doesnt get started.

Thanks in advance,

---

### Post by Cheesemill on 2013-06-13
On Ubuntu you also need to edit the MySQL AppArmor profile to give the MySQL daemon access to the new location.
I'm not on a Ubuntu machine with MySQL installed at the moment but I believe the file you need to edit is /etc/apparmor.d/usr.sbin.mysqld.

---

### Post by rahbz on 2013-06-13
Cheesemill, thanks for the update 
[http://stackoverflow.com/questions/1795176/how-to-change-mysql-data-directory](http://stackoverflow.com/questions/1795176/how-to-change-mysql-data-directory). I found this thread and eventually I wound up fixing the issue.

Thank you,

---

