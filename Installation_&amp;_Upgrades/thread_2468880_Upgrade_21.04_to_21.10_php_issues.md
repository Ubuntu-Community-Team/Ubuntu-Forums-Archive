---
title: "Upgrade 21.04 to 21.10 php issues"
date: 2021-11-12
forum: Installation &amp; Upgrades
---

### Post by w2vy on 2021-11-12
When upgrading i allowed the script to remove unused packages

I ended up with most things working fine (as far as I have noticed) but php8.0 was installed, the shell command provided the version but I could not run PHP web pages
I finally figured out I needed to add mod-php8.0 and then phpinfo() worked

My nextcloud (NC21) can not connect to the mysql database, I tried the configured values in the shell mysql command and I could connect

I am having problems getting any errors in syslog or apache log

Nextcloud has a php cronjob that I get the following error from

Doctrine\DBAL\Exception: Failed to connect to the database: An exception occurred in the driver: could not find driver in /var/www/nextcloud/lib/private/DB/Connection.php:87
Stack trace:
#0 /var/www/nextcloud/3rdparty/doctrine/dbal/src/Connection.php(1486): OC\DB\Connection->connect()
#1 /var/www/nextcloud/3rdparty/doctrine/dbal/src/Connection.php(1014): Doctrine\DBAL\Connection->getWrappedConnection()
#2 /var/www/nextcloud/lib/private/DB/Connection.php(231): Doctrine\DBAL\Connection->executeQuery()
#3 /var/www/nextcloud/3rdparty/doctrine/dbal/src/Query/QueryBuilder.php(210): OC\DB\Connection->executeQuery()
#4 /var/www/nextcloud/lib/private/DB/QueryBuilder/QueryBuilder.php(287): Doctrine\DBAL\Query\QueryBuilder->execute()
#5 /var/www/nextcloud/lib/private/AppConfig.php(344): OC\DB\QueryBuilder\QueryBuilder->execute()
#6 /var/www/nextcloud/lib/private/AppConfig.php(109): OC\AppConfig->loadConfigValues()
#7 /var/www/nextcloud/lib/private/AppConfig.php(300): OC\AppConfig->getApps()
#8 /var/www/nextcloud/lib/private/legacy/OC_App.php(961): OC\AppConfig->getValues()
#9 /var/www/nextcloud/lib/private/Server.php(685): OC_App::getAppVersions()

Any idea what may be missing from php?

Tom

---

### Post by MAFoElffen on 2021-11-13
This is just what I read: 
> "*Nextcloud* 21 *supports php8*.0. *Nextcloud* 20 does not."
What version of NextCloud are you running?

EDIT:
MySQL current version is 8.0.27 (not sure what is with 21.10) and MySQL8.0 was added as fully supported by PHP7.4... So I am assuming that is still supported in PHP8.

---

### Post by w2vy on 2021-11-14
I'm running 22.1.1

I also tried php7 same errors, so i'm going to dig up my old raid disk and look at the php install, maybe none of the modules were installed as part of the upgrade?

---

### Post by w2vy on 2021-11-14
I ran through all the php modules that I had on my system before upgrade (Thank God for Backups) and added the equivalent ones for php8, apache restart and all good.

Is it normal when upgrading php that the upgrade scripts don't consider php modules?

---

### Post by MAFoElffen on 2021-11-14
I'm thinking just like some Python libraries/modules and some additions I have added to applications... Especially extra's to some games and to Eclipse IDE add-ons... It see's the main package, but not things that are added within an application.

It see's installed "Packages"... but not things internally (that are not actually packages or from packages). I think this would be even more so (for me), If in Python3, if I had installed many things in PIP3. Those kinds of things would not be seen from an installer.
****
So this is now Solved? Please use the "solved" Link in the upper right of the page, under the Thread Tools, so that other users can find your solution.

---

### Post by w2vy on 2021-11-14
Well, You just "thinking" out loud may not be a real answer.

I guess I could open a bugzilla against the upgrade script to find out for sure, unless someone knows for sure that it is expected that when PHP upgrades all your old modules are just dropped on the floor.

---

