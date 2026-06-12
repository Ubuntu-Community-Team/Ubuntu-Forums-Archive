---
title: "GD is not activated or doesnt work"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by Zulan on 2008-11-10
Hi!

I have a few weeks old ubuntu server installed with LAMP. For some reason Joomla reports GD not to be installed. Also, [http://www.zulan.se/phpinfo.php](http://www.zulan.se/phpinfo.php) says it's not there. I have installed it using apt-get install php5-gd and it finishes successfully but still, Joomla reports the same problem and can't manipulate the images. I'm fairly new to linux so a detailed answer is much appreciated!

php -m says gd is there

Thanks!

---

### Post by Francewhoa on 2008-11-21
[FONT=Arial][SIZE=2]Same issue here with Ubuntu Server 8.04.1 and PHP5. The following worked for me. It will install a GD pre-compiled working version. It is a complete bundled (forked) GD libraries:
[/SIZE][/FONT]
[LIST=1]
[*][FONT=Arial][SIZE=2]If not already done removing your current GD package and its configurations.
[/SIZE][/FONT][SIZE=2]```
sudo apt-get --purge remove 
```[/SIZE][FONT=Arial][SIZE=2]

[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Adding 2 lines to your file /etc/apt/**sources.lst**
[/SIZE][/FONT][SIZE=2]```
deb http://packages.dotdeb.org stable all
deb-src http://packages.dotdeb.org stable all
```[/SIZE][FONT=Arial][SIZE=2]

[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Updating your current apt-get list[/SIZE][/FONT][SIZE=2]```
apt-get update
```[/SIZE]
[*][SIZE=2]Installing working GD package.
```
apt-get install php5-gd
```It will complain about non-authenticated sources, just ignore, it will also update some additional php libs.

When prompt select **keep_current** modified php.ini

[/SIZE]
[*][SIZE=2]Restarting Apache
```
/etc/init.d/apache2 restart
```Enjoy

Source: [http://drupal.org/node/134331#comment-983886](http://drupal.org/node/134331#comment-983886)
[/SIZE]
[/LIST]

---

### Post by fooey on 2009-02-06
awesome. after sever different solutions, yours is the only one that worked. thanks!

---

