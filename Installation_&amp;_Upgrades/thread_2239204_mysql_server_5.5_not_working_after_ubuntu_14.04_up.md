---
title: "mysql server 5.5 not working after ubuntu 14.04 update"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by alagiri-rajesh on 2014-08-12
[COLOR=#333333][FONT=UbuntuRegular]I had Ubuntu 14.04 installed on my system. I recently updated ubuntu and now my mysql does not start and workbench says that mysql server has been stopped. And when i try to start it gives me the following error[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]2014-08-12 23:02:04 - Checking server status... 2014-08-12 23:02:04 - Trying to connect to MySQL... 2014-08-12 23:02:04 - Can't connect to MySQL server on '127.0.0.1' (111) (2003) 2014-08-12 23:02:04 - Assuming server is not running 2014-08-12 23:02:04 - Server start done. 2014-08-12 23:02:04 - Checking server status... 2014-08-12 23:02:04 - Trying to connect to MySQL... 2014-08-12 23:02:04 - Can't connect to MySQL server on '127.0.0.1' (111) (2003) 2014-08-12 23:02:04 - Assuming server is not running[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]And also when i try to login using terminal (mysql -u root -p ) i get the following error:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have also tried to reinstall Ubuntu but i am unable to do so. Gives me the following error:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Reading package lists... Done Building dependency tree
Reading state information... Done mysql-server-5.5 is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have data which i have not taken backup of as i am unable to log into the server. I am a newbie please help me resolve this issue without losing my data.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Awaiting for your earliest response.[/FONT][/COLOR]

---

### Post by JetStorm on 2014-08-12
That error looks like it came from a mysql client and not the server.
What happens when you type 
**sudo service mysql start**

---

