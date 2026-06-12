---
title: "serious mysql problem after upgrade to 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by whitefawn on 2010-04-30
Morning people. I will appreciate any help here.

I upgraded from Kubuntu 9.10 to 10.04. 32 bit.

The  install had not finished as it barked at tripwire config. I have had to  stop it and continue from command prompt.

More or less the install went OK .
After the install,  mysql 5.1 does not want to start or stop. Commands

/etc/init.d/mysql stop  ( or 'stop mysql' , or service mysql stop' )
/etc/init.d/mysql start

do not finish - do not return to command prompt. No log messages insyslog or mysql logs.

say, I do 'service mysql start', the command does not return, I click Ctrl+C, then repeat the command. This displays : 'start: Job is already running: mysql'.  of course mysql is not running.

I've tried to remove and  reinstall the packages. No result. There is 'stop mysql' command in one  of install scripts that hangs.

Any solution that does not include reinstall ?

Thanks in advance for your help.
 							[IMG]http://kubuntuforums.net/forums/Themes/classic/images/icons/modify_inline.gif[/IMG]

---

### Post by mourngrym1969 on 2010-04-30
First, backup your data directories for MySQL (your actual databases)... that way, anything you do can be recovered from by just copying these back into their correct locations.

Once you do that, I would reinstall MySQL, making sure it does it completely:

'sudo apt-get install mysqlserver --fix-missing --fix-broken --assume-yes'

This will download and re-install the server. After that is complete, run through the initial mysql configuration (add your users, etc). After that, stop the server, copy over your data files to the old location and restart MySQL. If you created the same users with the same passwords, your databases should all start up and be useable.

Let me know if you have any questions or need more detail.

Mourn

---

### Post by whitefawn on 2010-04-30
I assume you've been talking about mysql-server. I tried it before, didn't help.

---

### Post by jaxson on 2010-05-02
Yes I have the same problem with mysql-server. I upgraded from Karmic where mysql-server was working properly. When I try to start or stop it just hangs until I kill it.
If I try to connect it gives:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

So it's obviously not running. I have not found anything in the logs(messages or syslog) for this either.

Point me in the right direction please.

---

### Post by bryxal on 2010-05-02
Same problem here.... if anyone has suggestions, I would love to hear them. This one was upgraded from Beta 2
there is no PID file. no process that I can find. Nothing gets written to either mysql.err or mysql.log.
somethings get written to syslog, I believe its with the debian sys admin permissions not working anymore..... I tried resetting those with a startup init file as per resetting the root password on mysql.com but still doesn't seem to work.

any other leads would be appreciated.

Thanks

---

### Post by vewert on 2010-05-03
I am having the same problem after upgrading from 9.10 to 10.04.  MySQL server does start on boot, and command hangs when I try to start and/or restart it.

I tried: 
sudo /etc/init.d/mysql start
sudo service mysql start
sudo mysqld

and maybe a few more along with the stop and restart equivalents and finally did manage to get it to start, but there is definitely a problem.

---

### Post by biffnix on 2010-05-03
Yes, please help.  I have the same problem, and it's huge!  My LAMP server (Karmic Koala) was upgraded this morning to Lucid, and MySQL fails.

If I type: /etc/init.d/mysql start

Then I see this:

Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start mysql start: Job failed to start

If I type: service mysql start

Then I get:

start: Job failed to start


If I just type: mysql

Then I get:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Please HELP!  My server is dead in the water until I can get MySQL back on its feet!

---

### Post by darkpills on 2010-05-04
Hello,

We had the same problem over here after the ubuntu upgrade.

We solved this by re-creating mysqld.pid with good rights :
```
touch /var/run/mysqld/mysqld.pid
```If it does not solve your problem, try the more verbose command:
```
sudo /usr/bin/mysqld_safe --user=mysql
```Good luck!

---

### Post by biffnix on 2010-05-04
> **darkpills said:**
> Hello,

We had the same problem over here after the ubuntu upgrade.

We solved this by re-creating mysqld.pid with good rights :
```
touch /var/run/mysqld/mysqld.pid
```If it does not solve your problem, try the more verbose command:
```
sudo /usr/bin/mysqld_safe --user=mysql
```Good luck!

When I tried: touch var/run/mysqld/mysqld.pid

I got: touch: cannot touch `/var/run/mysqld/mysqld.pid' : No such file or directory

When I tried: /usr/bin/mysqld_safe --user=mysql

I got: ```
root@squishbox:/var/run# /usr/bin/mysqld_safe --user=mysql
100504 09:43:17 mysqld_safe Logging to '/var/lib/mysql/squishbox.squish.us.err'.
100504 09:43:17 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
``` And now it's just sitting there.  I think mysqld_safe must be running, as Wordpress came back up (although the gallery2 links seem broken).  You can see for yourself at [http://www.squish.us](http://www.squish.us) .

So what do I do to make sure it launches at startup properly?  Still doesn't seem to be doing things correctly.

---

### Post by woj2tas on 2010-05-05
Try to run 

```
$ sudo mysqld_safe &
```

it will turn on Your database.

---

### Post by macsx82 on 2010-05-05
I've the same problem, but for me it seems work uninstall all mysql entries through synaptic an then reinstall using ```
sudo tasksel
``` and selecting the "LAMP" option. I tried to reboot my machine and mysql is still running!..

---

### Post by LordSaladin on 2010-05-06
I had the same problem when I upgraded, and just found an easy fix after a fair few hours trying all the suggestions on here and a load more from the IRC room.

It seems that the upgrade changed the permissions for the /etc/mysql/my.cfg file to be globally writeable. So, use 'gksudo nautilus' to change the permissions back to allowing only root to have write access.

Worked perfectly for me. Hopefully will be of some help to anyone else who is having the problem.

---

### Post by daveman67 on 2010-05-07
I upgraded from 9.10 to 10.04 and had the same problem - mysql not starting.

> **whitefawn said:**
> Morning people. I will appreciate any help here.
After the install,  mysql 5.1 does not want to start or stop. Commands

/etc/init.d/mysql stop  ( or 'stop mysql' , or service mysql stop' )
/etc/init.d/mysql start

do not finish - do not return to command prompt. No log messages insyslog or mysql logs.


Tried this to give me error messages.
```
sudo /usr/bin/mysqld_safe --user=mysql
```

and found this in syslog

```
May  7 12:03:22 saturn mysqld_safe: Starting mysqld daemon with databases from /home/dave/dev/data/mysql
May  7 12:03:22 saturn mysqld: 100507 12:03:22 [Warning] option 'thread_stack': unsigned value 128 adjusted to 131072
May  7 12:03:22 saturn mysqld: 100507 12:03:22 [Warning] The syntax '--log' is deprecated and will be removed in MySQL 7.0. Please use '--general_log'/'--general_log_file' instead.
May  7 12:03:22 saturn mysqld: 100507 12:03:22 [Warning] options --log-slow-admin-statements, --log-queries-not-using-indexes and --log-slow-slave-statements have no effect if --log_slow_queries is not set
May  7 12:03:22 saturn mysqld: 100507 12:03:22 [Note] Plugin 'FEDERATED' is disabled.
May  7 12:03:22 saturn mysqld: /usr/sbin/mysqld: Table 'mysql.plugin' doesn't exist
May  7 12:03:22 saturn mysqld: 100507 12:03:22 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
May  7 12:03:22 saturn mysqld: 100507 12:03:22  InnoDB: Started; log sequence number 0 2140736324
May  7 12:03:22 saturn mysqld: 100507 12:03:22 [ERROR] /usr/sbin/mysqld: unknown option '--skip-bdb'
May  7 12:03:22 saturn mysqld: 100507 12:03:22 [ERROR] Aborting
```

Clue was --skip-bdb. When I had run my upgrade I kept the /etc/mysql/my.cnf file, which contains 
```
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb

```
Commenting out that option allowed mysql to start again. Remaining errors in the log were fixed by running mysql_upgrade.

This thread was quite useful in pointing out the red herrings in the error output above. [http://lists.mysql.com/mysql/216042](http://lists.mysql.com/mysql/216042)

Cheers, Dave

---

### Post by Thomas Gutzmann on 2010-05-07
You may also have a look at [http://ubuntuforums.org/showthread.php?t=1475798](http://ubuntuforums.org/showthread.php?t=1475798).

HTH

Thomas

---

### Post by hotbelgo on 2010-05-09
[http://ubuntuforums.org/showpost.php?p=9177875&postcount=6](http://ubuntuforums.org/showpost.php?p=9177875&postcount=6)

---

### Post by mansonthomas on 2010-05-20
Hi,

 first use the service mysql start/stop instead of /etc/init.d/mysql...

normally if you user /etc/init.d script it complains and tell you to use 'service'.

ex: 

thomas@home:/etc/mysql$ sudo /etc/init.d/mysql status
[sudo] password for thomas:
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql status

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the status(8) utility, e.g. status mysql
mysql start/running, process 13020



I had a similar issue, of mysql starting and did not return the hand, if you try again you get a message that mysql is running while it's not.

The reason was that in /etc/mysql/my.cnf some directory, files (loggin, bin log, relay log) did not exists.

Also I had an issue on upgrade to 10.04 on a server : see this bug : 

[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/573318)

the /etc/mysql/my.cnf disappear on upgrade.

Regards,
Thomas.

---

### Post by jrble819 on 2010-05-27
I ran the command
```
sudo /usr/bin/mysqlrepair
```

and then everything start working again after running 
```
sudo restart mysql
```

---

### Post by barney_1 on 2010-06-05
Running mysqlrepair seems to have done the trick for me after upgrading to 10.04. Thank you!

---

### Post by JohnnyVW on 2010-06-05
> **jrble819 said:**
> I ran the command
```
sudo /usr/bin/mysqlrepair
```

and then everything start working again after running 
```
sudo restart mysql
```

Yay!  :guitar:

The above fixed it for me too!

---

### Post by dgavenda on 2010-09-16
Here's another thing to try.  It's worked on two servers that were upgraded from 9.10->10.04 and had this issue w/ mysql.  


1) Remove mysql: sudo apt-get remove mysql-core mysql-server-5.1 mysql-client-5.1 

2) sudo apt-get autoclean

3) Remove most mysql files:
sudo rm -fr /var/log/mysql*
sudo rm -fr /var/lib/update-rc.d/mysql*
sudo rm -fr /var/lib/dpkg/info/mysql-*
sudo rm -fr /var/lib/mysql/
sudo rm -fr /var/lib/dpkg/info/libmysqlclient1* 

4)sudo aptitude install mysql-server-5.1

5) Presto!  MySQL should be installed and working.

I did this process twice and it did take about ~8 hrs to 'find'.  So, hopefully, this will prevent someone else from wasting time on resolving this issue.  Also, this will delete any mysql db's you have/had.

---

### Post by satish_j on 2010-10-11
> **biffnix said:**
> 
When I tried: /usr/bin/mysqld_safe --user=mysql

I got: ```
root@squishbox:/var/run# /usr/bin/mysqld_safe --user=mysql
100504 09:43:17 mysqld_safe Logging to '/var/lib/mysql/squishbox.squish.us.err'.
100504 09:43:17 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
``` And now it's just sitting there.  I think mysqld_safe must be running, as Wordpress came back up (although the gallery2 links seem broken).  You can see for yourself at [http://www.squish.us](http://www.squish.us) .
Did you get it working??
iam facing this exact issue and still looking for solution.
Pls share the solution if you have solved it..

---

### Post by theDaveTheRave on 2010-11-08
Hello all,

I've had the same issue with my install of mysql since I upgraded.

I created a launchpad bug report [https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/666383]("https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/666383") with details of how I solved the problem. Essentially I re-installed from source.

here are some details to take into account...(copied from my 6th post on the bug report)


Can confirm that the installation from source is running as expected.

Please note that if you are going to do this you need to find the folder where your tables are kept (look into /usr/local/mysql/ data or they may appear somewhere in a subfolder of /var/ ~ probably a personal setting)

a quick run down of what you need to bear in mind.

- make sure you have all your old data tables saved somewhere, and a copy of your old my.cnf (this file will also tell you where you data tables are stored)


- if you are running some systems (eg drupal) they look for the mysql.sock file in a different location (ie not /tmp/mysql.sock) so you will need to create a symbolic link to the file for them to work, I assume that in the deb install / upgrade this not an issue?

- As you are installing from source you will need to insert mysql into /etc/init.d/ if you want it to run on boot up.

- to do this you need to run the following commands...

get chkconfig, as it isn't included in the newer version, as they are using upstart and not system-v init.d things.

```
   sudp apt-get install chkconfig 
```

the server start up script needs to be in the correct location...

```
   sudo cp /usr/local/mysql/mysql.server /etc/mysql
```

now you can insert mysql into the init.d[/code]

```
   sudo chkconfig --add mysql
```

then you need to tell the system to really run it...

```
   sudo update-rc.d mysql defaults
```

You will get error messages about the script now being an upstart job.

I used the docs on the mysql site for [install from source]("http://dev.mysql.com/doc/refman/5.1/en/binary-installation.html").

and information from [URL="http://ubuntuforums.org/showthread.php?t=1470738"]this thread
[/URL] to get mysql to run on boot.

I also read a multitude of other bug reports and forum threads (most of which are linked via my bug report and the above thread) so thanks to everyone else for suffering this problem with me.


This worked for me, hope it works for someone else also...

if there are any questions / changes, please contact me here, or via pm.

David

ps. just quickly, I recall that the only time I didn't have a problem installing mysql was when I did a clean install of a server system, and selected a 'lamp' server setup. Otherwise I've installed from source?

---

### Post by bdalzell on 2011-01-09
I have this problem since upgrading to Lucid in December 2010. I have tried all the suggestions in this thread and still I get the error:

mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

When I try to log into MySQL

I also read the long thread with the sticky on upgrading and how one should not stray from a standard install and expect the computer to work correctly. I suppose that thread's author thinks that LAMP is not part of a standard install.

Many people who are using a computer for any sort of business activity will be using a database. So considering LAMP to not be "standard" is not a good idea.

I purchased a new harddrive and tried to install Lucid directly to it. This resulted in my computer only being able to use "low graphics mode" despite it being fine with high resolution mode in Karmic and in the Lucid upgrade booting off of the original harddrive. It is an older computer. 

It seems to me that the problem is that MySQL is not able to access 

/var/run/mysqld/mysqld.sock

If anyone has any suggestions I would appreciate hearing them.

Since my db application is a single user one I am considering trying SQLite as I do have a copy of my db files stored in a separatel place. 

:confused:

---

### Post by theDaveTheRave on 2011-01-27
@bdalzell

I did notice something strange about the mysql.sock file, it seemed to have 'moved location' (or rather the sym link didn't work). This was the case for when I was trying to sugraCRM, it may be the same for you.

Have a double check of the documentation to confirm were it is 'supposed' to be and see if it tallies up with the location that your system is looking at. It took me an awful long time to realise this was why sugar wasn't working!

Also I guess you are installing from the repos, as far as I am concerned if you have installed from the repo's then that is a 'standard' install. And things should break in this way when upgrading.

But then that is the beauty of Linux...

If it ain't broke, break it!

David

---

### Post by SomeLikeItHot on 2011-03-07
> **bdalzell said:**
> I have this problem since upgrading to Lucid in December 2010. I have tried all the suggestions in this thread and still I get the error:

mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

When I try to log into MySQL

I also read the long thread with the sticky on upgrading and how one should not stray from a standard install and expect the computer to work correctly. I suppose that thread's author thinks that LAMP is not part of a standard install.

Many people who are using a computer for any sort of business activity will be using a database. So considering LAMP to not be "standard" is not a good idea.

I purchased a new harddrive and tried to install Lucid directly to it. This resulted in my computer only being able to use "low graphics mode" despite it being fine with high resolution mode in Karmic and in the Lucid upgrade booting off of the original harddrive. It is an older computer. 

It seems to me that the problem is that MySQL is not able to access 

/var/run/mysqld/mysqld.sock

If anyone has any suggestions I would appreciate hearing them.

Since my db application is a single user one I am considering trying SQLite as I do have a copy of my db files stored in a separatel place. 

:confused:

Hi there - I am currently running into the exact same problem (Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock')... 
Did you eventually solve this and if yes, how ?... 
Many thanks,
Joe

---

### Post by SomeLikeItHot on 2011-03-07
> **SomeLikeItHot said:**
> Hi there - I am currently running into the exact same problem (Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock')... 
Did you eventually solve this and if yes, how ?... 
Many thanks,
Joe

Just got it to work! 
Problem was = access rights of my.cnf file.
Changed to 644 (readable by all, writable by root) and that's it. 
SEE Lachlan Mulcahy post on [http://mysql.bigresource.com/Track/mysql-D9WEBenI/](http://mysql.bigresource.com/Track/mysql-D9WEBenI/)
Cheers

---

