---
title: "MySQL will not start"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by stevo81989 on 2010-05-03
I dont know. I have had tons of issues with the linux today. Now when I try and start mysql it just fails. the syslog says:


May  3 16:19:40 tp-inventory /etc/init.d/mysql[7783]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May  3 16:19:40 tp-inventory /etc/init.d/mysql[7783]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
May  3 16:19:40 tp-inventory /etc/init.d/mysql[7783]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
May  3 16:19:40 tp-inventory /etc/init.d/mysql[7783]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
May  3 16:19:40 tp-inventory /etc/init.d/mysql[7783]:
May  3 16:19:50 tp-inventory kernel: [ 1295.530016] parport0: FIFO is stuck
May  3 16:19:50 tp-inventory kernel: [ 1295.570018] parport0: BUSY timeout (1) in compat_write_block_pio

I have already tried to create and modify the /var/run/mysql folder. Doesnt work. When I type mysqld I get:


100503 16:21:01  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.


The command mysql results in:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I have even tried to uninstall mysql and reinstall it an nothing works. Any suggestions?

---

### Post by cavh on 2010-05-03
Have you had a MySQL installation running successfully on this machine? If so, what's changed on the machine recently? Have you changed any permissions?

You could try installing MySQL using the ```
sudo tasksel
``` command from a terminal and let us know how that goes (choose the LAMP server option - LAMP stands for Linux, Apache, MySQL and PHP)? Tasksel has a sweet LAMP install process - it all just works.

Before running tasksel, uninstall MySQL and all configuration files associated with it:

```
sudo apt-get purge mysql
```

---

### Post by stevo81989 on 2010-05-03
Yes, everything was working fine, until we had a power outage. i booted it back up. I was able to get it to work via a simple reinstall of mysql. Then I added a user and the mysql crashed. And so far this "taskel" installer is frozen on the mysql configure

---

### Post by cavh on 2010-05-04
Hmmm, the fact your machine suffered a power outage whilst running and the words in your original post to the effect that you've been having a ton of issues leads me to think that this might not be just a MySQL problem. However, first thing to do now is:

Check that your username is a member of the mysql group by going to System, then User & Groups, then click the key symbol with the label 'click to make changes', enter your password, then click the Manage Groups button, then scroll down to the mysql group, highlight it and click the Properties button to see the users in that group. Let us know if you appear as a member of that group.

Once you've done this, make sure the permissions for the mysqld folder are as is shown on the screenshot attached below (the far right one of the three).

Within the mysqld folder you should (presuming mysql is running) have two files - mysqld.pid and mysqld.sock. See the screenshots attached for their permissions.

The screenshots are taken from my machine on which MySQL is running fine.

If this doesn't work, I suggest you post again in the Server Platforms forum as the guys there will have more knowledge.

Good luck,

Clive

---

### Post by stevo81989 on 2010-05-04
Looks like I already gave that a shot, but I verified and it still didnt work. Thanks for all your help!

---

### Post by cavh on 2010-05-04
You're welcome, good luck! If the Server Platform guys can't solve it, you may need to back up your data and do a fresh Ubuntu install followed by tasksel. There seem to be a bug or two with MySQL and Lucid, so perhaps just use Karmic till that gets fixed (sorry, I don't have a bug report number, just remembering some posts I saw yesterday on the forums).

---

### Post by macsx82 on 2010-05-05
I've the same problem, but for me it seems work uninstall all mysql entries through synaptic an then reinstall using ```
sudo tasksel
``` and selecting the "LAMP" option. I tried to reboot my machine and mysql is still running!..

---

