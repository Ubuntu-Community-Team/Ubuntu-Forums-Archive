---
title: "[MySQL] MySQL can't connect after upgrading to 11.10 (ERROR 2002 (HY000))"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by guyfromfl on 2011-10-13
I just got finished upgrading, and testing all my software.  Everything has worked except MySQL Workbench, or the command client.

I changed my data directory to be stored /media/Storage/mysql so upgrading distros would be easier...

When I try to connect via terminal I get:
> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I have seen some similar questions out there, but none of the fixes I tried did anything, one way or the other.

If there is a log or conf file you want me to post, please let me know.

I am still some what a noob at linux, so any help would be great!

---

### Post by yazifeather on 2011-10-13
I'm having the same problem too! 

I tried restarting mysql via ```
sudo /etc/init.d/mysqld restart
``` but was instructed to use ```
service mysql stop/start
``` instead. When I try this, I get the following error message:
```

start: Rejected send message, 1 matched rules; type="method_call", sender=":1.79" (uid=1001 pid=8217 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

```


Any help would be appreciated.

---

### Post by JoGiz on 2011-10-14
Same problem for me!

Error.log is repeating the following message:

```
111014 12:16:13 [Note] Plugin 'FEDERATED' is disabled.
111014 12:16:13  InnoDB: Initializing buffer pool, size = 8.0M
111014 12:16:13  InnoDB: Completed initialization of buffer pool
111014 12:16:14  InnoDB: Started; log sequence number 44 3178763025
111014 12:16:14 [ERROR] Can't start server : Bind on unix socket: Permission denied
111014 12:16:14 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
111014 12:16:14 [ERROR] Aborting

111014 12:16:14  InnoDB: Starting shutdown...
111014 12:16:19  InnoDB: Shutdown completed; log sequence number 44 3178763025
111014 12:16:19 [Note] /usr/sbin/mysqld: Shutdown complete[/PHP]No other instance is running.
```

---

### Post by guyfromfl on 2011-10-14
When I try the command yazifeather suggested, I get the same error, and my log is identical to JoGiz...

It looks like we all have the same issue.

Anything else?  It looks like a permission issue on the dir mysql is trying to store the connection's socket.

can one of you run 
```
ls -al /var/run/
```
and tell me what the group and users are for mysqld?

Mine was mysql:root.  I changed the ownership to mysql:mysql but still have the same problem.

---

### Post by aaron10110 on 2011-10-14
```
drwxr-xr-x  2 mysql      root         60 2011-10-14 12:24 mysqld

```

---

### Post by guyfromfl on 2011-10-14
I have no clue what the problem is.  I changed back the permissions.

Anybody have any idea what the problem is?

I might try reinstalling mysql, I dont know what else to do..

This is the stuff about linux that frustrates the hell out of me...once its set up its a great os, but I'll be grey before i'm 31!

---

### Post by guyfromfl on 2011-10-14
...anybody???? i need this for work!  if not ill have to start using windows again..please help

---

### Post by tux43 on 2011-10-14
> **guyfromfl said:**
> ...anybody???? i need this for work!  if not ill have to start using windows again..please help

No - don't do that (go back to windows)

```

sudo chown mysql:mysql /var/run/mysqld/
service mysql stop
service mysql start

```

Worked for me, permissions are wrong post upgrade.

---

### Post by spindler on 2011-10-15
Well this is a rather nasty issue......

I tried the commands suggested by tux43 and received the following error.


$sudo mysql:mysql /var/run/mysqld
$service mysql stop

stop: Rejected send message, 1 matched rules; type="method_call", sender =":1.58" (uid=1000 pid=4173 comm="stop mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="sbin/init")

The when I typed: 

$service mysql stop

I get a similar message

start: Rejected send message, 1 matched rules; type="method_call", sender  =":1.59" (uid=1000 pid=4196 comm="stop mysql ")  interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)"  requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1  comm="sbin/init")

---

### Post by rfhutchins on 2011-10-15
> **spindler said:**
> Well this is a rather nasty issue......

I tried the commands suggested by tux43 and received the following error.


$sudo mysql:mysql /var/run/mysqld
$service mysql stop

stop: Rejected send message, 1 matched rules; type="method_call", sender =":1.58" (uid=1000 pid=4173 comm="stop mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="sbin/init")

The when I typed: 

$service mysql stop

I get a similar message

start: Rejected send message, 1 matched rules; type="method_call", sender  =":1.59" (uid=1000 pid=4196 comm="stop mysql ")  interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)"  requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1  comm="sbin/init")
type sudo in front of these two commands 
service mysql stop
service mysql start

---

### Post by spindler on 2011-10-15
Thanks a lot.... That was a rather silly mistake.

But it did not fix my problem.  The error did not go away.  :(


I did end up fixing the problem by reinstalling MYSQL.
[B]sudo apt-get install mysql-server


Here is a resource I used to help me.  [https://help.ubuntu.com/11.04/serverguide/C/mysql.html](https://help.ubuntu.com/11.04/serverguide/C/mysql.html)
[/B]

---

### Post by yazifeather on 2011-10-15
Thanks! Mine is working again :)

---

### Post by chkl on 2011-10-15
I have just downgraded from 11.10 back to 11.04. The upgrade was more or less a total disaster:
- MySQL was downgraded from 5.5 to 5.1 and stopped working.
- phpmyadmin stopped working.
In addition to this, my menus/Gnome desktop was thrown out and could only be reinstalled in a very limited fashion.
+ several other problems.

Who makes these decisions ? This is not the Ubuntu I have been using/upgrading since v. 8 (returning to Windows feels almost like an option ...).

/Christer

---

### Post by yazifeather on 2011-10-16
chkl,

Why would you downgrade?

---

### Post by Spudooli on 2011-10-16
I fought with this problem too and found it was apparmor that was preventing mysql from starting which is clear from syslog.

I got mysql running in the short term by running
 
sudo aa-complain /etc/apparmor.d/*

which prevents apparmor from stopping mysql running, but which is not a good long term solution.

I've removed the new apparmor rule usr.sbin.mysqld.dpkg-dist and restarted apparmor but it still won't let mysql run. I"m off hunting the solution to that now

---

### Post by JoGiz on 2011-10-17
Think I got it to work now..

in /etc/mysql/my.conf
and section [mysqld]

There was a port-change done. I dont know if I did this or not. But to my knowledge I have not changed ports.

It looked like this:
```
#port            = 3306
port           = 3307
```

This also resulted when disabling Apparmor that my JBoss connection failed.
Chaning it back to port 3306 solved my Jboss connection problem. 
```
port            = 3306
#port           = 3307
```

Mysql also staretd when Apparmor was enabled.

So check your my.conf and port-number to see if this portchange was made by me or the upgrade.

---

### Post by antonyhand on 2011-10-17
I tried for three days but thanks Spudooli your solution works...

sudo aa-complain /etc/apparmor.d/*

This works, after completely removing mysql and related files then using
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql

It was hanging installing mysql-server for 20 minutes but in a separate terminal window using the sudo aa-complain /etc/apparmor.d/* command caused the installation to complete and all is working again.

I hope there is a permanent fix out there somewhere.

---

### Post by venkatesh20 on 2011-10-19
I am also facing the same issue, just changing the permission is not working for me 
> while we are trying to find a fix, can anybody suggest me how to back up the data dir

---

### Post by firebadger on 2011-10-22
Same for me. I upgraded from Maverick to Natty then straight to Oneiric and didn't test on Natty. Not sure where problem crept in but apparmour complain mode working for now, nonetheless I'd really appreciate a longer term fix.

---

### Post by tumba25 on 2011-10-22
> **venkatesh20 said:**
> I am also facing the same issue, just changing the permission is not working for me 
> while we are trying to find a fix, can anybody suggest me how to back up the data dir
Just copy the directory /var/lib/mysql (IIRC that is the default place) to some safe location.

---

### Post by Romanik on 2011-10-27
> **guyfromfl said:**
> I just got finished upgrading, and testing all my software.  Everything has worked except MySQL Workbench, or the command client.

I changed my, [MySQL to MS SQL Server]("http://www.dbload.com") data directory to be stored /media/Storage/mysql so upgrading distros would be easier...

When I try to connect via terminal I get:


I have seen some similar questions out there, but none of the fixes I tried did anything, one way or the other.

If there is a log or conf file you want me to post, please let me know.

I am still some what a noob at linux, so any help would be great!
File: /mysql/plugin frm (errno: 13) 110403 17:28:52 error can t open the  mysql plugin table run mysql_upgrade connect : (hy000/2002): can t  connect to local mysql. Upgraded ubuntu, can t connect to mysql server -  server fault can t connect to local mysql server through socket /tmp  error 2002 (hy000): can t connect to local mysql server through socket  /tmp after that fails, i can start it.

---

### Post by nukeqler on 2011-11-01
> **Spudooli said:**
> I fought with this problem too and found it was apparmor that was preventing mysql from starting which is clear from syslog.

I got mysql running in the short term by running
 
sudo aa-complain /etc/apparmor.d/*

which prevents apparmor from stopping mysql running, but which is not a good long term solution.

I've removed the new apparmor rule usr.sbin.mysqld.dpkg-dist and restarted apparmor but it still won't let mysql run. I"m off hunting the solution to that now

Spudooli, you want to reverse the above change before doing what I suggest below.

Apparently the above apparmor file got some modifications when I upgraded from 11.04 to 11.10, but I foolishly rejected them when I did the upgrade.

To fix it, I did
 
```
sudo mv /etc/apparmor.d/usr.sbin.mysqld.dpkg-dist /etc/apparmor.d/usr.sbin.mysqld
sudo restart mysql
```

and I'm back in business.

Hope this helps.

---

### Post by dboy on 2011-11-02
Seeing other MySQL problems as well, such as MySQL Workbench not running under ubuntu 11.10. This ubuntu release is a mess. Do not use. If you upgraded or did fresh install I highly recommend reverting to 11.04.

---

### Post by EowynCarter on 2011-11-06
> **dboy said:**
> Seeing other MySQL problems as well, such as MySQL Workbench not running under ubuntu 11.10. This ubuntu release is a mess. Do not use. If you upgraded or did fresh install I highly recommend reverting to 11.04.

Yeah, what's up with mysql workbench ? :o :confused:

---

### Post by EowynCarter on 2011-11-06
After a bit of googleling on the myslq workbench issue

here :
[http://wb.fabforce.eu/?p=1217](http://wb.fabforce.eu/?p=1217)
[http://bugs.mysql.com/bug.php?id=62347](http://bugs.mysql.com/bug.php?id=62347)
[https://launchpad.net/~olivier-berten/+archive/misc](https://launchpad.net/~olivier-berten/+archive/misc)

---

### Post by heedrox on 2011-11-08
Thanks nukeqler, that worked for me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

> **nukeqler said:**
> Spudooli, you want to reverse the above change before doing what I suggest below.

Apparently the above apparmor file got some modifications when I upgraded from 11.04 to 11.10, but I foolishly rejected them when I did the upgrade.

To fix it, I did
 
```
sudo mv /etc/apparmor.d/usr.sbin.mysqld.dpkg-dist /etc/apparmor.d/usr.sbin.mysqld
sudo restart mysql
```and I'm back in business.

Hope this helps.

---

### Post by o100ja on 2012-05-10
Try the following code (it worked for me)
```

sudo su
su mysql
service mysql restart

```

---

### Post by velko on 2012-05-14
here is a fix:

[https://bugs.launchpad.net/ubuntu/+source/mysql-5.5/+bug/934013/comments/9](https://bugs.launchpad.net/ubuntu/+source/mysql-5.5/+bug/934013/comments/9)

please create an account there and click the "I am affected too link in the top bug area."

thanks.

---

### Post by guyfromfl on 2012-05-15
I tried all of the fixes above, and still get "Start:Job failed to start"

---

