---
title: "Installing Cacti 0.8.7a on Ubuntu 7.10 Server"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by wfrutiger on 2007-11-23
These instructions are a modification of the instruction in thread [http://ubuntuforums.org/showthread.php?t=616553]("http://ubuntuforums.org/showthread.php?t=616553"). Follow all other directions omiting section **Get Cacti and install it**.
 
**Get Cacti and install it**
Create a temporary folder 
*mkdir /cacti*
*cd /cacti/*
 
Download Cacti Version 0.8.7 … web address may have changed
*wget [http://www.cacti.net/downloads/cacti-0.8.7a.tar.gz](http://www.cacti.net/downloads/cacti-0.8.7a.tar.gz)*
 
Unzip Download
*tar xzvf cacti-0.8.7a.tar.gz*
 
Move folder to /usr/share/
*mv /cacti/cacti-0.8.7a /usr/share/cacti*
 
Set permissions on rra/ and log/ folders
*cd /usr/share/cacti*
*chown -R www-data:www-data rra/ log/*
 
Edit /etc/crontab and add the following line:
*/5 * * * * www-data php /usr/share/cacti/poller.php > /dev/null 2>&1 
 
Restart Cron
*/etc/init.d/cron restart*
 
Edit /etc/php5/apache2/php.ini set memory_limit value:
memory_limit=128m
 

[COLOR="Red"]To fix the broken graph template: SNMP - Generic OID Template[/COLOR]
Click *Graph Templates*
Click *SNMP - Generic OID Template*
Set Lower Limit Value to *0*.

---

### Post by jsidhu on 2008-03-18
a few notes that might help some people:

I've got this up and running with 0.8.7b

To instlal cacti, follow directions: [http://docs.cacti.net/node/447](http://docs.cacti.net/node/447)

To install the missing packages:

apt-get install rrdtool
apt-get install snmp
apt-get install snmpd

---

