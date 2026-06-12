---
title: "Installing Cacti Version 0.8.7 on Ubuntu 7.10 Server"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by wfrutiger on 2007-11-18
**Install Needed Packages**
*apt-get update*
*apt-get install mysql-server apache2 php5 php5-cli php5-mysql php5-mysql php5-snmp libapache2-mod-php5 rrdtool snmp*
*apt-get update*
*apt-get upgrade*
 
**Get Cacti and install it**
Create a temporary folder 
*mkdir /cacti*
*cd /cacti/*
 
Download Cacti Version 0.8.7 … web address may have changed
*wget [http://www.cacti.net/downloads/cacti-0.8.7.tar.gz](http://www.cacti.net/downloads/cacti-0.8.7.tar.gz)*
 
Unzip Download
*tar xzvf cacti-0.8.7.tar.gz*
 
Move folder to /usr/share/
*mv /cacti/cacti-0.8.7 /usr/share/cacti*
 
Set permissions on rra/ and log/ folders
*cd /usr/share/cacti*
*chown -R www-data:www-data rra/ log/*
 
Edit /etc/crontab and add the following line:
*/5 * * * * www-data php /usr/share/cacti/poller.php > /dev/null 2>&1 
 
Restart Cron
*/etc/init.d/cron restart*
 
Edit /etc/php5/apache2/php.ini set memory_limit value:
memory_limit=128m
 
**Configure Apache**
Edit /etc/apache2/sites-avaliable/default change DocumentRoot value to:
DocumentRoot /usr/share/cacti
 
Restart Apache
*/etc/init.d/apache2 restart*
 
**Setup MySql Database**
Create the cacti database
*mysqladmin -u root create cacti -p*
 
Pipe Database Script in to mysql to create tables; cacti.sql can be found in the cacti folder
*mysql cacti < cacti.sql -u root -p *
 
Logon to mysql
mysql -u root -p
 
Setup cacti database permissions:
*GRANT ALL ON cacti.* TO cactiuser@localhost IDENTIFIED BY '[COLOR=red]somepassword[/COLOR]';*
*flush privileges;*
*exit*
 
Edit cacti config file for Mysql /usr/share/cacti/include/config.php:
$database_type = "mysql";
$database_default = "cacti";
$database_hostname = "localhost";
$database_username = "cactiuser";
$database_password = "[COLOR=red]somepassword[/COLOR]";
$database_port = "3306";
 
"[COLOR=red]somepassword[/COLOR]" This can be set to any password
 
 
Alright! If you made it this far cacti should be ready to go! Open browser and point it to your server. Default username/password is admin/admin.

---

### Post by Gouki on 2007-12-19
Great post! Congratulations.

Just a small note to people new to CACTI. The default username and password (used after all the instructions provided above) is 'admin' for both the user and password.

You will be FORCED to change this after the first login.

Note: Did you guys know that VODAFONE uses cacti? :) Got some inside information about their usage of cacti and nagios. Way to go, Vodafone!

---

### Post by cjblade54 on 2008-03-03
Awesome post.  Got it to work on my first try.  :lolflag:

---

### Post by cjblade54 on 2008-03-03
I just recently installed Cacti.  Everything went just fine 'til the point where i tried to pull the graph from one of the network switches.  I used the graphic debug and this message came up:
RRDTool Says:

ERROR: opening '/usr/share/cacti/rra/fine_art_core_switch_traffic_in_10.rrd': No such file or directory


It seems like its not generating the graph .... any help?

---

### Post by Scormen on 2008-03-11
Hi all,

I'm having the same problem like cjblade54: **....... cacti/rra/fine_art_core_switch_traffic _in_10.rrd': No such file or directory**

Is there a way to fix this?

Thanks,
Kris

---

