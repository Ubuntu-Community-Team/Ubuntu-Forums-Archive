---
title: "apt-get hangs when upgrading mysql-server-5.1"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by exodar on 2010-06-20
When I attempt to do the following:

```
sudo apt-get update
sudo apt-get upgrade
```

on my Ubuntu Server 10.04 installation, it hangs at the following line:

```
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.1 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_i386.deb)
```

I cannot even CTRL-C out of it!  I end up having to kill my session and log in from a different terminal and the upgrade process is still running.  I have rebooted it several times and when I go back and try again it tells me:

```
E: dpkg was interrupted, you must manually run 'sudo --configure -a' to correct the problem.
```

Once I do that I am back at square one and it freezes up when I try to upgrade mysql.

Thanks...

---

### Post by nebajoth on 2010-07-13
Bump ^.  This is happening to me as well.  Did you find a fix?

---

### Post by hymerman on 2010-08-04
I'm getting the exact same thing. I've fiddled about all over the place but I can't get it to work. I've managed to uninstall it but on installing it it hangs in the same way.

It looks like it's hanging whilst waiting to start/stop the mysql service - "ps aux | grep mysql" always shows either "stop mysql" or "start mysql". Killing those processes makes the upgrade/installation continue with an error. Note that I can start/stop the services manually just fine.

---

### Post by cyberedsun on 2010-08-14
I am also facing this issue. I even tried to re-install the system and did the upgrade when the issue happened again.

Please help to give out solution.
Thanks.

---

### Post by jaya28inside on 2010-08-19
exactly!

I encounter the same
like u all experienced....

got stuck at this line...

> 
Setting up mysql-client-core-5.1 (5.1.41-3ubuntu12.6) ...
Setting up mysql-client-5.1 (5.1.41-3ubuntu12.6) ...
Setting up mysql-server-core-5.1 (5.1.41-3ubuntu12.6) ...
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.6) ...
Installing new version of config file /etc/init/mysql.conf ...



and until now... already 10 minutes passed
still stuck.
still hang over there.

I wonder, perhaps this is because the previous action I did
was... removing the mysql-server via this unhealthy way...

```

root# : apt-get remove mysql-server
... Later I choose Yes.

```

```

root# : apt-get remove mysql-client
... Later I choose Yes.

```

and Thus, it's done removed.
but still the trash is still everywhere...
rather than using 

```

root# : apt-get remove --purge mysql-server

```

OMG.
then If I'm not mistaken, 
without realizing my mistakes previously,
I continue to execute this command

```

root# : apt-get install mysql-server

```

which is yes,,, getting stuck until now. :( Any Idea?

---

### Post by AnRkey on 2010-09-21
I have the same issue, I will post the answer if I fix mine.

---

### Post by weller99 on 2010-10-25
I ran into the same problem.

I just renamed /etc/init.d/mysql.conf to /etc/init.d/mysql.conf.bak
and then reran apt-get upgrade and it worked ;)

---

### Post by MichaelNW on 2010-12-05
> **weller99 said:**
> I ran into the same problem.

I just renamed /etc/init.d/mysql.conf to /etc/init.d/mysql.conf.bak
and then reran apt-get upgrade and it worked ;)

Depending on whether or not upstart is implemented on your system the file may also be 

[INDENT]   /etc/init/mysql.conf[/INDENT]

As weller99 pointed out, renaming this file to another name will allow the upgrade to run to completion.

---

### Post by flickerfly on 2011-01-26
I did a full purge, restart everything and then tried again.
```

Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up mysql-server-core-5.1 (5.1.41-3ubuntu12.9) ...
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.9) ...

```

I then ran this command with these results in another terminal and came back to the other terminal to find it had completed.
```
$ sudo start mysql
mysql start/running

```

Then I tried to stop and start it using upstart and otherwise
```
$ sudo stop mysql
stop: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist

$ sudo start mysql
start: Unknown job: mysql

$ sudo service mysql stop
<insert msg about using upstart />

$ sudo service mysql start
<insert msg about using upstart />
start: Unknown job: mysql

```

If I try to run mysql I get error 2002. What's going on?

```
$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

I noticed that after the reinstall, the /etc/init/mysql file wasn't replaced so I then dropped it back in place and things got weirder.
```
$ sudo mv /etc/init/mysql.conf.backup /etc/init/mysql.conf

$ sudo start mysql 
^C //it froze and I forced it to quit

$ sudo mv /etc/init/mysql.conf /etc/init/mysql.conf.backup

$ sudo start mysql 
mysql start/running

$ sudo stop mysql
stop: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist

$ sudo start mysql 
start: Unknown job: mysql

```

So I understand that to mean, I can put the file back in place, fail, remove the file and it'll start. Then I can fail to stop it because something with dbus isn't around. Then the I try start again and it not only can't start but doesn't know mysql exists and all I've done since last time is try to stop it. 
:confused:

Can someone explain what is going on?

---

### Post by gramoun_kal on 2011-11-07
Same happened to me after my machine froze while mysql was installing. I finished the install after a hard-reset, but I hit the same issue.

I tried apt-get purge 'ing all the packages starting with 'mysql' and reinstalling afresh, no success. I tried renaming the /etc/init/mysql.conf, still no success.

The problem seemed to be that the root account was corrupter or something, but was not reset by a reinstall.

In the end, I found where mysql keeps its users (including "root"): In a bunch of files in /var/lib/mysql. I apt-get purge 'd all mysql packages, deleted this folder (but you might want to rename it instead, just in case it contained something you'd miss: sudo mv /var/lib/mysql /var/lib/mysql-backup

When I reinstalled mysql, it set me up a new fresh, pristine root account for mysql. Hurray.

---

### Post by Rocketeer on 2012-01-25
Any news on this? I had similar problems, but purging, removing and cleaning did not help. During reinstall I recieve now 

Quote:
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
Regards

---

### Post by thale on 2012-02-27
Fixed it.

I purged all of the mysql packages, cleaned the cached deb's, removed the mysql user, removed the /var/lib/mysql /etc/mysql /etc/init/mysql.conf /etc/init.d/mysql blah blah

everything. However, I missed the /var/run/mysql/mysql.sock AND there was a mysql zombie process that wouldn't respond to kill -9. I had to reboot the machine. After all that I was able to reinstall mysql.

---

### Post by deepesh on 2012-03-17
I faced the same problem. Stopping mysql server let the upgrade proceed. 
$sudo service mysql stop

---

