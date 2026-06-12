---
title: "Upgraded server from 11.04 to 11.10"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by nariub on 2011-12-28
upgraded from 11.04 to 11.10
it wasn't as clean as it should have been

did online upgrade via the update-manager.. went ok

changed the greeter background and my desktop background to match. Because I am retentive about such things

[http://www.omgubuntu.co.uk/2011/09/tool-change-lightdm-wallpaper-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/09/tool-change-lightdm-wallpaper-ubuntu-11-10/)


```
gksu gedit /etc/lightdm/unity-greeter.conf
```

changed to:
/usr/share/backgrounds/Power_of_Words_by_Antonio_Litterio.jpg
 
from:
/usr/share/backgrounds/warty-final-ubuntu.png

noticed I had all the users on the box displayed 
including smbguest and something new.. a plain guest?
 I say wtf?

stopped the greeter from displaying guest 
and from displaying a list of users at all..
now you need username and password to log in at the console
actually told it to suppress the guest.. 
not really sure if entering guest as a username would have failed if i did not do that?

----------------
[http://askubuntu.com/questions/68953/dont-list-all-users-at-login-with-lightdm](http://askubuntu.com/questions/68953/dont-list-all-users-at-login-with-lightdm)

suppress the userlist.

greeter-hide-users=true


```
sudo vi /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false
greeter-hide-users=true
```


---------
changed ICON size and stuff by searching for about:config and dinking about with it..  uses CCSM (compiz settings manager)
I didnt copy the url for that one..

----------
webpages and squirrelmail worked fine
but mediawiki and tikiwiki did not..  

grrr...  mysql and apparmor


[http://my.opera.com/djfake/blog/2011/11/05/ubuntu-11-10-mysql-problem-after-upgrade](http://my.opera.com/djfake/blog/2011/11/05/ubuntu-11-10-mysql-problem-after-upgrade)

```
  /{,var/}run/mysqld/mysqld.pid w,
  /{,var/}run/mysqld/mysqld.sock w,

```

```
sudo vi /etc/apparmor.d/usr.sbin.mysqld

  /var/log/mysql/* rw,
# /var/run/mysqld/mysqld.pid w,
# /var/run/mysqld/mysqld.sock w,
# after upgrade to 11.10
  /{,var/}run/mysqld/mysqld.pid w,
  /{,var/}run/mysqld/mysqld.sock w,
  /sys/devices/system/cpu/ r,

sudo service apparmor restart

sudo service mysql restart

```
and the wiki's were back..

--------------
cron was spamming me with the following php5 error message

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/idn.so' - /usr/lib/php5/20090626/idn.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/sqlite.so' - /usr/lib/php5/20090626/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

[http://ubuntuforums.org/showthread.php?t=1610097](http://ubuntuforums.org/showthread.php?t=1610097)

rename would have worked.

but i liked this one 

sudo bzip2 /etc/php5/conf.d/idn.ini
sudo bzip2 /etc/php5/conf.d/sqlite.ini


[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/875262](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/875262)

cd /etc/php5/conf.d/
sudo mv sqlite.ini sqlite.NOTini


$ ls /etc/php5/conf.d/
curl.ini  imagick.ini  memcache.ini  pdo.ini         recode.ini   tidy.ini
gd.ini    imap.ini     ming.ini      pdo_mysql.ini   snmp.ini     xmlrpc.ini
gmp.ini   ldap.ini     mysqli.ini    pdo_sqlite.ini  sqlite3.ini  xsl.ini
idn.ini   mcrypt.ini   mysql.ini     pspell.ini      sqlite.ini

$ sudo bzip2 /etc/php5/conf.d/idn.ini
$ ls /etc/php5/conf.d/
curl.ini     imagick.ini  memcache.ini  pdo.ini         recode.ini   tidy.ini
gd.ini       imap.ini     ming.ini      pdo_mysql.ini   snmp.ini     xmlrpc.ini
gmp.ini      ldap.ini     mysqli.ini    pdo_sqlite.ini  sqlite3.ini  xsl.ini
**idn.ini.bz2**  mcrypt.ini   mysql.ini     pspell.ini      sqlite.ini

$ sudo bzip2 /etc/php5/conf.d/sqlite.ini
$ ls /etc/php5/conf.d/
curl.ini     imap.ini      mysqli.ini      pspell.ini      tidy.ini
gd.ini       ldap.ini      mysql.ini       recode.ini      xmlrpc.ini
gmp.ini      mcrypt.ini    pdo.ini         snmp.ini        xsl.ini
**idn.ini.bz2**  memcache.ini  pdo_mysql.ini   sqlite3.ini
imagick.ini  ming.ini      pdo_sqlite.ini  **sqlite.ini.bz2**


so i zipped em up which changed their names...
and i had to wait for 30 minutes to see if it worked.

and she worked..


-------------


found this on the second day...
```
Dec 28 11:57:00 HOSTNAME postfix/smtpd[XXX]: NOQUEUE: reject: RCPT from mail-iy0-f180.google.com[209.85.210.180]: 451 4.3.5 Server configuration problem; from=<XXXXX@gmail.com> to=<XXXXX@MYDOMAIN.NET> proto=ESMTP helo=<mail-iy0-f180.google.com>
```

```
$ netstat -nlpa | grep 10023
(No info could be read for "-p": geteuid()=1000 but you should be root.)
tcp6       0      0 ::1:10023               :::*                    LISTEN      -               
```
$ sudo vi /etc/default/postgrey 

old
POSTGREY_OPTS="--inet=10023"
new
POSTGREY_OPTS="--inet=127.0.0.1:10023"

$ sudo service postgrey restart
 * Stopping postfix greylisting daemon postgrey                          [ OK ] 
 * Starting postfix greylisting daemon postgrey                          [ OK ] 

```
$ netstat -nlpa | grep 10023
(No info could be read for "-p": geteuid()=1000 but you should be root.)
tcp        0      0 127.0.0.1:10023         0.0.0.0:*               LISTEN      -               

```
Only a guess here but it appears the old way only applies to ipv6 now..?
curious..

---

