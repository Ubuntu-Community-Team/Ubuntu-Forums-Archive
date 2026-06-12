---
title: "Mythbuntu - Secondary Backend Setup"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by BigPacks on 2010-12-29
Hi,

I'm trying to get a secondary mythbuntu backend running but I'm having problems getting it to connect.  I've been looking around and trying to figure out what to do but I'm not having much luck.

These machines all sit behind a firewall, so they should all be able to see each other.  Also I've assigned static IP addresses to all these machines.

Is this all I need to do?

[LIST=1]
[*]In the *MythTv Backend Setup* -> *General*. set the local backend and master backend both to the ip address of the machine.  I.e. to 192.168.0.X.
[*]Edit */etc/mysql/my.cnf* and put a # in front of **bind-address = 127.0.0.1**
[*]Restart MySQL with the following command: ```
sudo service mysql restart
```
[*]Edit MySQL```
mysql -u root mythconverg -p
```
[*]Running the following command in MySQL```
grant all on mythconverg.* to mythtv@"192.168.0.%" identified by "mythtv";
```
[*]Quit MySQL
[*]Edit MySQL```
mysql -u root -p
```
[*]Running the following command in MySQL```
set password for 'mythtv'@'192.168.0.%' = password('XXXXXXXX');
``` where XXXXXXXX is the SQL password.
[*]Quit MySQL
[/LIST]

When I start the secondary backend, should I be able to see the MythTV if I enter the correct IP address and database password?   Am I missing something to get this working?

When I run MySQL commands (step 5 & 8), it says that 0 rows have been affected.  I'm not sure why?  In step 1 I've configured the IP address of the backend?  I'm not sure if this is THE problem or a problem.



Thanks

---

