---
title: "cannot connect to MySQL db through Drupal"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by ubscott on 2010-12-24
hi,

i'm in the process of migrating from Drupal 5 to Drupal 6.  My main Drupal page won't load.  I have been stepping through the index.php Eclipse and XDebug.  The error I'm receiving is:

"can't connect to local MySQL server through socket '/tmp/mysql.sock'"

i've been reading a lot about the error, such as in these two sites:
[http://answers.yahoo.com/question/index?qid=20061221214154AAvsf4y](http://answers.yahoo.com/question/index?qid=20061221214154AAvsf4y)
[http://ubuntuforums.org/archive/index.php/t-386056.html](http://ubuntuforums.org/archive/index.php/t-386056.html)

some things i've tried to do are:
sudo chown mysql:mysql /var/run/mysqld

i've also successfully logged into the mysql database via:
mysql -uroot -p

from mysql, i have tried: \s

The output includes this line:
/var/run/mysqld/mysqld.sock

so, it seems that my MySQL installation expects to put the sock file in /var/run/mysqld/mysqld.sock

however, my Drupal installation is trying to put it here:
/tmp/mysql.sock

that's my guess, anyways.

I have opened up:
/etc/mysql/my.cnf

it has several lines that references the sock file.  in the client section, it says:
port        = 3306
socket        = /var/run/mysqld/mysqld.sock

i think the sock file setting is correct; it matches what the MSQL control panel has.

First question: if my.cnf says the sock file is in /var/run/mysqld, why do I keep getting the error that it can't open /tmp/mysql.sock?  How do I tell Drupal to use '/var/run/mysqld/mysqld.sock'?

Second question: the mysql command-line interface (i.e., after i have logged into mysql from the terminal) doesn't mention a port from the listing obtained by entering '\s'.  is it possible that 3306 is a mistake?  (I have tried commenting out the port reference and i still get the error identified at the top of the thread.)

does anyone have any ideas about how to resolve the 'sock' error?  Many thanks if you do.  Merry Christmas, too.

---

### Post by ubscott on 2010-12-24
hi,

i'm in the process of migrating from Drupal 5 to Drupal 6.  My main  Drupal page won't load.  I have been stepping through the index.php  Eclipse and XDebug.  The error I'm receiving is:

"can't connect to local MySQL server through socket '/tmp/mysql.sock'"

i've been reading a lot about the error, such as in these two sites:
[http://answers.yahoo.com/question/in...1214154AAvsf4y]("http://answers.yahoo.com/question/index?qid=20061221214154AAvsf4y")
[http://ubuntuforums.org/archive/index.php/t-386056.html](http://ubuntuforums.org/archive/index.php/t-386056.html)

some things i've tried to do are:
sudo chown mysql:mysql /var/run/mysqld

i've also successfully logged into the mysql database via:
mysql -uroot -p

from mysql, i have tried: \s

The output includes this line:
/var/run/mysqld/mysqld.sock

so, it seems that my MySQL installation expects to put the sock file in /var/run/mysqld/mysqld.sock

however, my Drupal installation is trying to put it here:
/tmp/mysql.sock

that's my guess, anyways.

I have opened up:
/etc/mysql/my.cnf

it has several lines that references the sock file.  in the client section, it says:
port        = 3306
socket        = /var/run/mysqld/mysqld.sock

i think the sock file setting is correct; it matches what the MSQL control panel has.

First question: if my.cnf says the sock file is in /var/run/mysqld, why  do I keep getting the error that it can't open /tmp/mysql.sock?  How do I  tell Drupal to use '/var/run/mysqld/mysqld.sock'?

Second question: the mysql command-line interface (i.e., after i have  logged into mysql from the terminal) doesn't mention a port from the  listing obtained by entering '\s'.  is it possible that 3306 is a  mistake?  (I have tried commenting out the port reference and i still  get the error identified at the top of the thread.)

does anyone have any ideas about how to resolve the 'sock' error?  Many thanks if you do.  Merry Christmas, too.

---

### Post by ubscott on 2010-12-24
sorry, i accidentally posted my issue twice.

---

### Post by ubscott on 2010-12-28
hi,

i've been reading more about the problem and thought i'd come back here again with my begging bowl held out proudly.  

first, here's some related links:
[http://forums.mysql.com/read.php?11,51166,125142#msg-125142](http://forums.mysql.com/read.php?11,51166,125142#msg-125142)
[http://drupal.org/node/7410](http://drupal.org/node/7410)
[http://answers.yahoo.com/question/index?qid=20061221214154AAvsf4y](http://answers.yahoo.com/question/index?qid=20061221214154AAvsf4y)
[http://www.linuxforums.org/forum/servers/76122-mysqld-sock-missing.html](http://www.linuxforums.org/forum/servers/76122-mysqld-sock-missing.html)
[http://ubuntuforums.org/showthread.php?t=140036](http://ubuntuforums.org/showthread.php?t=140036)
[http://ubuntuforums.org/showthread.php?t=111292](http://ubuntuforums.org/showthread.php?t=111292)

there seems to be a few people who can't get MySQL to connect to  tmp/mysql.sock .  In my case, I am attempting to debug the index.php  file in my Drupal 6 installation directory.  (It has a 'page not found'  error.)  I am using Eclilpse and Xdebug.

I can connect to MySQL via phpMyAdmin and by the command line.  I just  can't do so with Drupal; specifically, my newly migrated (from Drupal 5)  Drupal 6 version.

from running MySQL in the command line, my version of MySQL is using:
/var/run/mysqld/mysqld.sock

in my starter post I mention that i already have edited my.cnf:
/etc/mysql/my.cnf

it didn't do any good.  I have also made sure to turn off 'write'  permissions "for the world" for cnf, on the theory that the file was  being disregarded because the permissions set were a security threat.

i've been trying to create a symbolic link.  i try:
cd /var/run/mysqld
sudo ln -s /tmp/mysql/

i don't receive an error message.  however, nothing comes of it.  (I still get the error.)

I go into my tmp folder:
cd /var/run/mysqld

the file that is in this folder is actually named ysqld.sock, not mysqld.sock.

i've tried to associate this file with the file that Drupal expects:
cd /var/run/mysqld
sudo ln -s ysqld.sock /tmp/mysql/mysql.sock

this gives me the error:
creating symbolic link `/tmp/mysql/mysql.sock': No such file or directory

i don't have a file named mysql.sock in /tmp/mysql

anyone with an idea of what should i try next?  all help is appreciated.  thanks.

---

### Post by ubscott on 2010-12-30
hi,

i've spent the last four nights trying to figure to figure out what to do about this damn 'mysql.sock' problem.  (I can't connect to MySQL via Drupal.  However, i can do this with phpMyAdmin and in the terminal window.  I am using Eclipse, XDebug and Ubuntu 10.04.)

the problem could be that my 'sock' file is actually named:
 /var/run/mysqld/ysqld.sock

somehow during installation I dropped the leading 'm' in 'mysqld.sock'.

I've tried copying the file to:
/var/run/mysqld/mysqld.sock.  

i get this error:
cannot stat `ysqld.sock': No such file or directory.

no file or directory?  (Ubuntu, i see ysqld.sock fine when i do "ls"...)

for the following files i have changed the name of my socket; i.e., I renamed 'mysqld.sock' to be 'ysqld.sock'. 

/etc/mySQL/my.cnf
/etc/mySQL/debian.cnf
/etc/

restart Apache.  shut down and restart Eclipse.  (I have Eclipse + XDebug + Ubuntu 10.04.)

having done these things i still can't get Drupal to connect to the correct socket.  i keep getting:
Can't connect to local MySQL server through socket '/tmp/mysql.sock

Mon dieu!  forgive me, but i wish i could get the immediate gratification that Windows provides (i.e., applications that install) along with the freedom and stability that a built Linux system gives you.  this Drupal 5 to Drupal 6 migration that i'm trying to finish makes the Lewis and Clark expedition seem like a Coors Light beach party.

it seems that i can reinstall mysql so that i get a file named 'mysqld.sock'.  i'm trying to avoid reinstallation because i'm not sure if doing so i will lose the my existing MySQL databases.

does anyone have any advice?  thanks,

---

### Post by ubscott on 2010-12-31
updates...

i see a mysqld.sock file now at:
/var/run/mysqld/mysqld.sock

i swear i saw ysqld.sock before!  i attempted to copy the ysqld.sock file to mysqld.sock, and got errors both times i tried it.  then i changed the /etc/mysql/my.cnf, the php.ini and the debian.cnf to all point to the correct sock location.

I also followed instructions found on this page:
[http://ubuntuforums.org/archive/index.php/t-386056.html](http://ubuntuforums.org/archive/index.php/t-386056.html)

regarding the section: "My problem (Ubuntu) was a permission issue on /var/run/mysqld..." I changed the permissions of the folder several ways, eventually to rwxrwxrwx.  When I run the Drupal index page on my local server, i no longer see the "mysqld.sock" error on that page.  Groovy!  However, I can't login.  In addition, when i attempt to use Xdebug and Eclipse to step through the index.php file of the local Drupal installation the mysql.sock error returns.

so, i have a mysqld.sock file in /var/run/mysqld.  This sock file is referenced in php.ini, my.cnf and debian.cnf.  I can connect to MySQL just fine in the terminal's command line.  However, it is just Drupal that won't get it.

In a few hours the calendar's year changes.  Have a nice New Year, everyone.

---

### Post by ubscott on 2011-01-04
i don't know how it happened, but suddenly i can login to the local site.  i changed the settings.php and default.settings.php files so that the $db_url variable attempted to use another account besides the root.  it didn't work.  so, i changed it back to what it was originally, restarted Apache and suddenly, i can login.

this took a couple of weeks, but i'm glad that Drupal finally figured out what was needed.  thanks for reading.

---

### Post by ubscott on 2011-01-12
well, being able to login to my local installation seems to have nothing to with the MySQLD.sock file ierror I see when i run XDebug on Ubunto 10.04.  i simply can't connect Drupal to the correct socket file.

I've been posting on all the popular forums, but cannot get anyone to help so far.  Development has been stopped for weeks as a result.

the current thread is where i identified the problem.  I cannot convince Drupal to look in a different place other than /tmp for the MySQLD.sock file.  I've tried editing all of the config files that seem relevant to the task (i.e., my.cnf, debian.cnf and php.ini).  I've told all these config files where the socket file is.

i've also posted my issue on the Drupal forum:
[http://drupal.org/node/1012364#comment-3897390](http://drupal.org/node/1012364#comment-3897390)

...as well as the MySQL forum:
[http://forums.mysql.com/read.php?10,402559,402559#msg-402559](http://forums.mysql.com/read.php?10,402559,402559#msg-402559)

but you may notice from my MySQL post  that my frustration is high.

I've lost three weeks to this issue.  Can't someone please offer some insight?

thanks.

---

### Post by ubscott on 2011-01-17
hi,

I backed up my MySQL databases. Then i tried to reinstall mysql.  I am still having a Mysqld.sock problem.

I have found this thread helpful:
[http://ubuntuforums.org/showthread.php?t=111292](http://ubuntuforums.org/showthread.php?t=111292)

i did a ps -A and found mysqld in the list.  I killed the process id for it.

now i am trying to run 'mysqld_safe'; i.e.,
cd /usr/bin
mysqld_safe

I get this output:
110117 22:06:46 mysqld_safe Logging to syslog.
110117 22:06:46 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
rm: cannot remove `/var/run/mysqld/mysqld.sock': Permission denied
rm: cannot remove `/var/lib/mysql/mps-desktop.pid': Permission denied
110117 22:06:49 mysqld_safe mysqld from pid file /var/lib/mysql/mps-desktop.pid ended

the permissions for the mysqld.sock file are:
cd /var/run/mysqld
ls -l yields:
srwxrwxrwx 

Does anyone know why a file with permissions set to 'srwxrwxrwx' gives me a 'Permission denied' error when I attempt to run mysqld_safe?

Does anyone have a good way to rebuild my mysqld.sock file so that Drupal can work with it?

Any help is appreciated.  thanks.

---

### Post by ubscott on 2011-01-23
hi,

for weeks now i have been trying to solve a problem that is preventing my local installation of Drupal from communicating to a MySQL database thanks to the UNIX sock file. 

I have posted about this problem on several forums, with no reply yet:
[http://drupal.org/node/1012364](http://drupal.org/node/1012364)
[http://forums.mysql.com/read.php?10,402559,402559](http://forums.mysql.com/read.php?10,402559,402559)

since my last post on this thread I have reinstalled the mysql common files.  i attempted to reinstall mysql server using Synaptic.  After reinstallation of mysql server i still see my MySQL databases.  

i can't login to mysql. from the terminal:
mysql status

this gives me the infamous "can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"

when i attempt to stop mysql via:
sudo mysql stop

I also get that message.


i found this informative page:
[http://ubuntuforums.org/showthread.php?t=111292](http://ubuntuforums.org/showthread.php?t=111292)

i try:
find / -name mysql.sock

i get hundreds of lines of output, most of which have a "permission denied" error; e.g.,
/var/lib/mysql/__MYSQL_DB_Name': Permission denied

(I removed the name of the database from the string.  this is the physical location for the database.)


the /var/run/mysqld folder has these permissions:
drwxrwxr-x  mysql  root

so i appear to have the correct folder permissions on this folder for the sock file to work.

i have set the this folder's permissions to:
/var/lib/mysql
drwxrwxrwx 34 mysql         mysql         4096 2011-01-23 17:59 mysql

(it was: drwxr_xrwx)


i have tried stopping and restarting mysql:
sudo mysql stop
sudo mysql start

initially, i could do these commands without getting an error.  however, lately i'm getting the infamous "can't connect...sock file" error.

when i try this:
service mysql restart

i get this message:
Rejected send message, 1 matched rules; type="method_call", sender=":1.69" (uid=1000 pid=12908 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

this command seems to work:
mysqld_safe

i get three messages saying the mysql daemon is being started and "mysqld_safe mysqld from pid file <file name>" ended

However, it doesn't work well enough for the stop/start commands to avoid that sock file problem.


Finally, in my mysqld folder i see no files:
/var/run/mysqld

i don't see the mysqld.sock file anymore.  I did about two hours ago.


It is hard to be positive about Ubuntu when you encounter show-stopping, maddening errors like the UNIX sock file issue.  

Any help is appreciated.  Don't be shy!

---

### Post by ubscott on 2011-02-03
Hi,

I finally found a solution that works for my local installation of Drupal.  I want to share it so that the next person doesn't experience the frustration i went through.

this thread was invaluable:
[http://drupal.org/node/7620](http://drupal.org/node/7620)

i changed my settings file like this:
$db_url = 'mysql://root@Password@localhost: port:/var/run/mysqld/mysqld.sock/database_name';

note that contrary to what the poster offered on that thread, i did not URL-encode this string.

In addition, i modified the database.mysql.inc:
function db_connect($url) {
  $url = parse_url($url);
  
  ...

  // Allow for non-standard MySQL port.
  if (isset($url['port'])) {
    $url['host'] = $url['host'] .':'. $url['port'];
  }

<NEW>

/** Added to allow socket file in path; last path element becomes DB name *****/  
$p = explode('/', $url['path'] );  
$plen = count($p);  
if ($plen > 1) {    
$url['path'] = '/' . array_pop($p);    
$url['host'] = $url['host'] .':'. join('/', $p);  } 

</NEW>


This technique works, and i am so relieved that Drupal can now connect to the MySQL database.

---

