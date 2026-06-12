---
title: "Xampp: Mysql Not Running"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by hemi519 on 2011-08-17
Hi All,

I am struck with this problem since yesterday, Everything was working fine until i got a sudden error saying 

[COLOR=#FF0000][FONT=Trebuchet MS][Warning]: PDO::__construct() [[pdo.--construct]("http://support.notionink.com/support1243/admin/pdo.--construct")]: [2002] No such file or directory (trying to connect via unix:///opt/lampp/var/mysql/mysql.sock) (Database/class.SWIFT_Database.php:330)

Then i went into server and restarted server. it started saying

 /opt/lampp/lampp restart
Stopping XAMPP for Linux 1.7.4...
XAMPP: Stopping Apache with SSL...
XAMPP: XAMPP-MySQL is not running.
XAMPP: XAMPP-ProFTPD is not running.
XAMPP stopped.
Starting XAMPP for Linux 1.7.4...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Couldn't start MySQL!
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.

I have tried almost every possible forum. they said to change permissions and i did everything , i rebooted, i am still getting the problem. can anyone help me
[/FONT][/COLOR]

---

### Post by raja.genupula on 2011-08-17
[http://www.linuxquestions.org/questions/linux-newbie-8/lampp-wont-start-apache-another-web-server-daemon-running-ubuntu-9-10-a-793807/](http://www.linuxquestions.org/questions/linux-newbie-8/lampp-wont-start-apache-another-web-server-daemon-running-ubuntu-9-10-a-793807/)


adopt the concept for your problem

---

### Post by hemi519 on 2011-08-17
i already saw that, but that could not help to solve my issue. I am using xampp server

when i tried to run this command

ls -la /opt/lampp/var/mysql

it is giving me following output


total 45412
drwxrwxrwx 8 root   root        4096 Aug 17 06:28 .
drwxrwxrwx 6 root   root        4096 Aug  5 07:45 ..
drwxrwxrwx 2 root   nogroup    12288 Jul  4 12:05 products
-rwxrwxrwx 1 root   root      128673 Aug 17 06:28 products.err
-rwxrwxrwx 1 nobody root      112964 Aug 16 13:03 Sproducts.err.save
drwxrwxrwx 2 root   root        4096 Mar 23  2007 cdcol
-rwxrwxrwx 1 root   nogroup  5242880 Aug 17 06:28 ib_logfile0
-rwxrwxrwx 1 root   nogroup  5242880 Aug 15 11:56 ib_logfile1
-rwxrwxrwx 1 root   nogroup 35651584 Aug 17 06:28 ibdata1
drwxrwxrwx 2 root   root        4096 Jan 10  2011 mysql
-rwxrwxrwx 1 root   root           5 Jan 10  2011 mysql_upgrade_info
drwxrwxrwx 2 root   root        4096 Jan 10  2011 performance_schema
drwxrwxrwx 2 root   root        4096 Aug  4  2010 phpmyadmin
drwxrwxrwx 2 root   root        4096 May  4  2010 test

---

