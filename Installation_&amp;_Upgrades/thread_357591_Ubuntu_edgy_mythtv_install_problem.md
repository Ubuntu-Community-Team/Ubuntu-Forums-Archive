---
title: "Ubuntu edgy mythtv install problem"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by williammanda on 2007-02-09
I have tried to install mythtv several times and end up with the same problem:

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-09 19:58:22.311 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-09 19:58:27.521 Unable to connect to database!
2007-02-09 19:58:27.521 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-09 19:58:27.591 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-09 19:58:27.645 Failed to init MythContext, exiting.
william@PIV-2-8:/etc$ 

This is the latest url I tried:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Go down to: Installing Myth TV (this is the meat of the installation)

sudo apt-get install mysql-server

i get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pwgen libxml-libxml-common-perl libqt3-mt-mysql libxml-namespacesupport-perl
  libjack0.100.0-0 libxml-libxml-perl libxml-sax-perl libxml-simple-perl
  libqt3-mt
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/25.0MB of archives.
After unpacking 67.5MB of additional disk space will be used.
Do you want to continue [Y/n]?  Y

Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 90219 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.24a-9_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.24a-9_all.deb) ...
Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [ ok ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up mysql-server (5.0.24a-9) ...
william@PIV-2-8:/$ 

Next step:
sudo apt-get install mythtv mythtv-themes

I get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxml-libxml-common-perl libxml-namespacesupport-perl libxml-libxml-perl
  libxml-sax-perl libxml-simple-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmyth-0.20 mythtv-backend mythtv-common mythtv-database mythtv-frontend
Suggested packages:
  mythweb mythmusic mythweather mythgallery mythdvd mythvideo mythgame
  msttcorefonts
Recommended packages:
  mythtv-doc xmltv-util
The following NEW packages will be installed:
  libmyth-0.20 mythtv mythtv-backend mythtv-common mythtv-database
  mythtv-frontend mythtv-themes
0 upgraded, 7 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/28.7MB of archives.
After unpacking 55.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

I get:
Preconfiguring packages ...
Selecting previously deselected package libmyth-0.20.
(Reading database ... 91698 files and directories currently installed.)
Unpacking libmyth-0.20 (from .../libmyth-0.20_0.20-0.2ubuntu2_i386.deb) ...
Selecting previously deselected package mythtv-common.
Unpacking mythtv-common (from .../mythtv-common_0.20-0.2ubuntu2_all.deb) ...
Selecting previously deselected package mythtv-database.
Unpacking mythtv-database (from .../mythtv-database_0.20-0.2ubuntu2_all.deb) ...
Selecting previously deselected package mythtv-frontend.
Unpacking mythtv-frontend (from .../mythtv-frontend_0.20-0.2ubuntu2_i386.deb) ...
Selecting previously deselected package mythtv-backend.
Unpacking mythtv-backend (from .../mythtv-backend_0.20-0.2ubuntu2_i386.deb) ...
Selecting previously deselected package mythtv.
Unpacking mythtv (from .../mythtv_0.20-0.2ubuntu2_all.deb) ...
Selecting previously deselected package mythtv-themes.
Unpacking mythtv-themes (from .../mythtv-themes_0.20-0.1_all.deb) ...
Setting up libmyth-0.20 (0.20-0.2ubuntu2) ...

Setting up mythtv-common (0.20-0.2ubuntu2) ...
adduser: Warning: that home directory does not belong to the user you are currently creating

Setting up mythtv-database (0.20-0.2ubuntu2) ...

Setting up mythtv-frontend (0.20-0.2ubuntu2) ...

Setting up mythtv-backend (0.20-0.2ubuntu2) ...
udev active, devices will be created in /dev/.static/dev/
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.

Setting up mythtv (0.20-0.2ubuntu2) ...
Setting up mythtv-themes (0.20-0.1) ...
william@PIV-2-8:/$ 

Next step:
sudo passwd mythtv

I get:
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
william@PIV-2-8:/$ 
I entered mythtv as the password

Next:
admin:x:106:garry,mythtv
I get:
william@PIV-2-8:/$ admin:x:106:william,mythtv
bash: admin:x:106:william,mythtv: command not found
william@PIV-2-8:/$ 
I try sudo:
william@PIV-2-8:/$ sudo admin:x:106:william,mythtv
sudo: admin:x:106:william,mythtv: command not found
william@PIV-2-8:/$ 
I'm not sure what to do here but to change the /etc/group file and add mythtv to everything I see that I am setup for.

william@PIV-2-8:/$ cd /etc
william@PIV-2-8:/etc$ sudo nano group

root:x:0:root,william,mythtv
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:william,mythtv
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,william,mythtv
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,william,mythtv
floppy:x:25:haldaemon,william,mythtv
tape:x:26:
sudo:x:27:
audio:x:29:william,mythtv,mythtv
dip:x:30:william,mythtv
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:william,mythtv
sasl:x:45:
plugdev:x:46:haldaemon,william,mythtv
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
ssl-cert:x:104:cupsys
crontab:x:105:
ssh:x:106:
messagebus:x:107:
avahi:x:108:
lpadmin:x:109:william,mythtv
haldaemon:x:110:
scanner:x:111:cupsys,hplip,william,mythtv
slocate:x:112:
gdm:x:113:
william:x:1000:root,william,mythtv
admin:x:114:william,root,mythtv
mythtv:x:116:william,root
ntp:x:115:
mysql:x:117:root,william,mythv

save and close

Next:
mythtv-setup

Then I get the 3 screens with a blue background: 1st screen - select language 2nd screen - setup database info (mythconverg, user and password). 3rd screen - custom id and wake on lan.

This isn't the only install I have used and they all result ib the same thing. I'm not a linux person but I'm willing to learn. But this is driving me nuts....
Please help. Once I get this one setup I want to setup another as a slave backend.
Thanks

---

### Post by basketcase on 2007-02-09
>  /var/lib/mythtv$ sudo /etc/cron.daily/mythtv-backend
Password:
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open


I'm getting these same errors on my build tonight.  First time I ever saw them too with all the installs I've tried in the past.

---

### Post by Staach on 2007-02-10
*sigh* I get the same problem as "williammanda"!! Please can someone help us out here?:(

---

### Post by williammanda on 2007-02-10
Well I got mythtv to work somewhat.
I found this:
[http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html)
and I did the following:
Debian 3.0

    $ mysql < mc.sql

Then I started mythtv-setup and I got the usual setup screens. Then I started the backend and then the frontend. I could only do all of this by being the super user. I can not log in as mythtv yet.
Thanks

---

### Post by williammanda on 2007-02-11
Well besides not being able to login as mythtv....things are working well. It seems that from what I got out of this whole situation is....don't use any guides that compile code...only use the binary files. Also doing the two steps concerning mysql. 
My pcHDTV 5500 wasn't supported in Edgy, so I'm working on setting up mythtv in Feisty since the kernel is newer. I will let you know how it goes.

---

### Post by croccodillo on 2007-02-15
Hi all,

I had the same problem during the installation of MythTV (now working perfectly).
[THIS]("https://help.ubuntu.com/community/MythTV") is the main page for the Ubuntu MythTV community; I followed the guide for frontend/backend system and now itis working great.
The error you refer to is explained and solved in the installation troubleshooting section, [HERE]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting?highlight=%28troubleshootin%29").

The most important line in your output is this:
> Access denied for user 'mythtv'@'localhost' (using password: YES)

Basically, you must start mysql (sudo mysql) and then update the user list in it, using the syntax reported in the troubleshooting.

Ciao,
Giovanni

---

