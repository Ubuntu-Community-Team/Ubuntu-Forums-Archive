---
title: "Usgraded to 10.04 - MySQL not connecting"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by wagb278 on 2010-05-30
I installed 10.04 (64-bit) and it is running. I installed LAMP using "tasksel" on this desktop that I also use as a server on my LAN for a few Web-enabled applications. Browsers on the LAN can display a test index.html file in the web root, but no database apps can connect to the MySQL databases. 

I am looking for ideas for how to fix this.

Everything was working on ubuntu 8.04 LTS, and still is. I have a dual boot with 8.04 and 10.04. When I set up this machine I established partitions for /Home, /Data (where the Databases and WWW files reside) - so either Ubuntu version can access those. After LAMP install I altered various files to have Apache and MySQL point to the directories on /data, vice the default locations.  I am pretty sure I got all those changed correctly.

When I try "mysql" in a terminal I get an error saying it cannot connect using a mydql.socket giving the path for which there is no socket file there (or anywhere on the 10.04 system).

Version 8.04 has the socket file in /var/run/mysqld, but that directory is empty on 10.04.

I noticed the user Group ID numbers are different between the to systems and I am sure that enters into my problem.  It may be the cause of not having a mysqld.sock file (install didn't have permissions to write that file - maybe).

Is there a way to force the GID numbers/group names to match between two installs of Ubuntu? 

I am a little reluctant to just go messing with group IDs without understanding possible hidden impacts of doing that.

Again - any ideas will be appreciated.

---

