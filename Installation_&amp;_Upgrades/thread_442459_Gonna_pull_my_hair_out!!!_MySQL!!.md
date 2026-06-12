---
title: "Gonna pull my hair out!!! MySQL!!"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by superyounan1 on 2007-05-13
one day mysql decided to start giving me this error:

```

error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```

There are lots of threads with solutions, but they all require logging into the mysql command line interface, the problem is mysql's root account password is not working any more either!!

I tried removing, purging, reinstalling mysql, but the problem doest go away! Is there are honest-to-goodness good way to completely wipe mysql off my computer, as if it was never there??? 

this is ridiculous, mysql is better behaved in windows! shame!

---

### Post by bukwirm on 2007-05-13
Try uninstalling mySQL, then removing all files in the dircetory /etc/mysql (be careful with rm).

---

### Post by superyounan1 on 2007-05-13
> **bukwirm said:**
> Try uninstalling mySQL, then removing all files in the dircetory /etc/mysql (be careful with rm).


thanks for the reply. I tried what you suggested, and it didnt work. I tried uninstalling it via synaptic but it failed in the middle of the process, turns I cant stop the process, so i checked it myself:

```

sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                           [fail] 

```

and immediately after i get that little update notifier in my panel, except its not suggesting an update, its telling me that there is some serious error preventing any updates, installs, and removes, and recommends that I run "apt-get install -f" to fix it. When I do that... guess what, it the bits of mysql that were just removed before the script failed.

I'm stuck, I cat get mysql to work, and now I cant even remove it

---

### Post by mlind on 2007-05-13
Post the log entry containing the error why mysql fails to uninstall. /var/log/syslog or ~/.xsession-errors (or /var/log/dpkg.log) should contain the error.

---

### Post by cvi on 2007-05-13
Hello,
The reason it is complaining about debian-sys-maint'@'localhost' is that the password for that mysql user has been changed from what debian/ubuntu originally set for it in its password file located in /etc/mysql/debian.cnf. The password in that file has to be the same as it the password for the debian-sys-maint user in the mysql database itself.


To get by the unable to log in as root problem

First stop your mysql server from running: 'sudo /etc/init.d/mysql stop' or sending 
then run 'sudo mysqld_safe --skip-grant-tables &'
this will allow you to bypass the password prompts so that you can reset the password for root, etc
then type 'mysql -u root'  without a password to enter the mysql console
to change the root password
then exit the console and stop the mysql server to start it the normal way again 'sudo /etc/init.d/mysql start'


After you run the apt-get install -f. You can try reinstalling the mysql-server.

sudo apt-get install --reinstall mysql-server

---

### Post by superyounan1 on 2007-05-13
Hi emlind, thanks for replying. I wasnt sure how much of the files to include, so I grabbed large chunks, sorry about that. My ~/.xsession-errors didnt have anything

> **mlind said:**
> Post the log entry containing the error why mysql fails to uninstall. /var/log/syslog or ~/.xsession-errors (or /var/log/dpkg.log) should contain the error.

```

cat /var/log/syslog | tail -n 150 | grep mysql


May 13 13:51:06 ubuntu-laptop mysqld_safe[16041]: Fatal error: Can't remove the pid file: /var/run/mysqld/mysqld.pid
May 13 13:51:06 ubuntu-laptop mysqld_safe[16043]: Please remove it manually and start /usr/bin/mysqld_safe again
May 13 13:51:06 ubuntu-laptop mysqld_safe[16045]: mysqld daemon not started
May 13 13:52:41 ubuntu-laptop mysqld_safe[16892]: A mysqld process already exists
May 13 13:52:55 ubuntu-laptop mysqld_safe[17054]: Fatal error: Can't remove the pid file: /var/run/mysqld/mysqld.pid
May 13 13:52:55 ubuntu-laptop mysqld_safe[17056]: Please remove it manually and start /usr/bin/mysqld_safe again
May 13 13:52:55 ubuntu-laptop mysqld_safe[17058]: mysqld daemon not started
May 13 13:53:10 ubuntu-laptop mysqld_safe[17235]: A mysqld process already exists
May 13 14:00:32 ubuntu-laptop mysqld_safe[21040]: A mysqld process already exists
May 13 14:01:57 ubuntu-laptop mysqld_safe[21829]: A mysqld process already exists
May 13 14:15:18 ubuntu-laptop mysqld_safe[28555]: A mysqld process already exists
May 13 17:41:44 ubuntu-laptop mysqld_safe[4553]: A mysqld process already exists
May 13 17:42:00 ubuntu-laptop /etc/init.d/mysql[4899]: 1 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May 13 17:42:00 ubuntu-laptop /etc/init.d/mysql[4899]: Could not open required defaults file: /etc/mysql/debian.cnf
May 13 17:42:00 ubuntu-laptop /etc/init.d/mysql[4899]: Fatal error in defaults handling. Program aborted
May 13 17:42:00 ubuntu-laptop /etc/init.d/mysql[4899]: 

```

```

cat /var/log/dpkg.log | grep mysql


2007-05-13 17:23:10 status config-files mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:23:10 status config-files mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:23:10 status config-files mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:23:10 status not-installed mysql-client-5.0 <none>
2007-05-13 17:28:49 install mysql-common <none> 5.0.38-0ubuntu1
2007-05-13 17:28:49 status half-installed mysql-common 5.0.38-0ubuntu1
2007-05-13 17:28:52 status unpacked mysql-common 5.0.38-0ubuntu1
2007-05-13 17:28:52 status unpacked mysql-common 5.0.38-0ubuntu1
2007-05-13 17:28:54 install libmysqlclient15off <none> 5.0.38-0ubuntu1
2007-05-13 17:28:54 status half-installed libmysqlclient15off 5.0.38-0ubuntu1
2007-05-13 17:28:56 status unpacked libmysqlclient15off 5.0.38-0ubuntu1
2007-05-13 17:28:57 status unpacked libmysqlclient15off 5.0.38-0ubuntu1
2007-05-13 17:28:57 install libdbd-mysql-perl <none> 3.0008-1build1
2007-05-13 17:28:57 status half-installed libdbd-mysql-perl 3.0008-1build1
2007-05-13 17:28:59 status unpacked libdbd-mysql-perl 3.0008-1build1
2007-05-13 17:28:59 status unpacked libdbd-mysql-perl 3.0008-1build1
2007-05-13 17:28:59 install mysql-client-5.0 <none> 5.0.38-0ubuntu1
2007-05-13 17:28:59 status half-installed mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:29:08 status unpacked mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:29:08 status unpacked mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:29:09 status unpacked mysql-common 5.0.38-0ubuntu1
2007-05-13 17:29:10 status unpacked mysql-common 5.0.38-0ubuntu1
2007-05-13 17:29:10 status half-configured mysql-common 5.0.38-0ubuntu1
2007-05-13 17:29:10 status installed mysql-common 5.0.38-0ubuntu1
2007-05-13 17:29:10 status unpacked libmysqlclient15off 5.0.38-0ubuntu1
2007-05-13 17:29:10 status half-configured libmysqlclient15off 5.0.38-0ubuntu1
2007-05-13 17:30:17 status installed libmysqlclient15off 5.0.38-0ubuntu1
2007-05-13 17:30:17 status unpacked libdbd-mysql-perl 3.0008-1build1
2007-05-13 17:30:17 status half-configured libdbd-mysql-perl 3.0008-1build1
2007-05-13 17:30:18 status installed libdbd-mysql-perl 3.0008-1build1
2007-05-13 17:30:18 status unpacked mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:30:18 status half-configured mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:30:18 status installed mysql-client-5.0 5.0.38-0ubuntu1
2007-05-13 17:34:57 status installed mysql-admin-common 1.2.5rc-1
2007-05-13 17:34:57 remove mysql-admin-common 1.2.5rc-1 1.2.5rc-1
2007-05-13 17:34:57 status half-configured mysql-admin-common 1.2.5rc-1
2007-05-13 17:34:57 status half-installed mysql-admin-common 1.2.5rc-1
2007-05-13 17:34:58 status config-files mysql-admin-common 1.2.5rc-1
2007-05-13 17:34:58 status config-files mysql-admin-common 1.2.5rc-1
2007-05-13 17:34:58 status config-files mysql-admin-common 1.2.5rc-1
2007-05-13 17:34:58 status not-installed mysql-admin-common <none>
2007-05-13 17:40:37 install libapache2-mod-auth-mysql 4.3.9-2.1ubuntu2 4.3.9-2.1ubuntu2
2007-05-13 17:40:37 status half-installed libapache2-mod-auth-mysql 4.3.9-2.1ubuntu2
2007-05-13 17:40:39 status unpacked libapache2-mod-auth-mysql 4.3.9-2.1ubuntu2
2007-05-13 17:40:39 status unpacked libapache2-mod-auth-mysql 4.3.9-2.1ubuntu2
2007-05-13 17:40:40 status unpacked libapache2-mod-auth-mysql 4.3.9-2.1ubuntu2
2007-05-13 17:40:41 status unpacked libapache2-mod-auth-mysql 4.3.9-2.1ubuntu2
2007-05-13 17:40:41 status half-configured libapache2-mod-auth-mysql 4.3.9-2.1ubuntu2
2007-05-13 17:40:41 status installed libapache2-mod-auth-mysql 4.3.9-2.1ubuntu2

```



Hey CVI, thanks for replying, 
> First stop your mysql server from running: 'sudo /etc/init.d/mysql stop' or sending
then run 'sudo mysqld_safe --skip-grant-tables &'

stopping mysql will not work, see my second post on this thread. 

and if I run `sudo mysqld_safe --skip-grant-tables &` I get:
```

[7] 24222
ubuntu@ubuntu-laptop:~$ mysqld_safe[24266]: A mysqld process already exists

```

and it does this even after a fresh restart and logging into the "safe gnome" session.

I have since ran `apt-get install -f` and regained the mysql files that were removed during the attempt to uninstall

and about reinstalling mysql:
```

 sudo apt-get install --reinstall mysql-server

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.5kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com feisty/main mysql-server 5.0.38-0ubuntu1 [47.5kB]
Fetched 47.5kB in 2s (17.3kB/s)   
Selecting previously deselected package mysql-server.
(Reading database ... 166366 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1_all.deb) ...
 * Stopping MySQL database server mysqld                                                                                                                       [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: error processing /var/cache/apt/archives/mysql-server_5.0.38-0ubuntu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server_5.0.38-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I have to say I really appreciate everyone looking at this and taking a stab at it, the ubuntu community is very active and friendly.

This whole mess started when i closed my laptop's screen as I was moving it, when I opened it again, the screen stayed black and the sytem wasnt responding at all, so i power-cycled it and got an error while booting, it told me run a command to check to file system (i dont remember teh details at all), it found numerous errors that it tried to fix. When it finished and rebooted, I was able to log in again... thats when mysql went south

---

### Post by superyounan1 on 2007-05-13
i made some progress, I ran

```
ps -e
```

and killed everything that had mysql in the name, that allowed me to stop mysql and use synaptic to do complete removals and I verified that /etc/mysql is empty.

Now I will follow this how-to to install mysql for apache, which is the same as the one I did the first time:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_for_Apache_HTTP_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_for_Apache_HTTP_Server")

I will post results

---

### Post by cvi on 2007-05-13
hello again,

The mysql server starts up from the init scripts, so it will run even if gnome is in safe mode. Regarding the sysmaint problem. I've done that before, it normally happens when I was setting one of the mysql user passwords and forgot to include the 'where' part of the sql statement. :oops: 

Try one of the following to stop the server:
1.sudo  cat /var/run/mysqld/mysqld.pid (it should return the process id of the mysql server if its running) 
Then type 'sudo kill ' and the number you got from the command above

2. Type ps ax and look for the process id of the mysql server. Then type 'kill ' and the process # from the first column.


Then try one of the apt-get commands to reinstall /remove etc.

If it still won't complete, you can try 

dpkg --remove mysql-server


When the computer was running the filesystem check, did it run a short check (a couple of minutes or less) or was it a full filesystem check?

Hope it helps

---

### Post by superyounan1 on 2007-05-13
> **cvi said:**
> hello again,
When the computer was running the filesystem check, did it run a short check (a couple of minutes or less) or was it a full filesystem check?


It did a short one, after which it told me that it was unable to fix the problem(s) and told me to manually run a certain command, unfortunately I forgot what it was. I remember it kept outputting i-node information, which peaked my interest because I took a systems programming course a year and a half ago and we discussed how inodes are implemented, etc.

Anyway, I did ps -e | grep mysql and got the pids for all they mysql processes, there was two. I kill -9'nd them and retried the same removal methods I've been trying, except this time they worked!

I did get nervous during the reinstall, it got stuck while it was trying to start mysql, but seems to be working fine now, i can log in!!!:KS 

whats really confusing and irritating me though is that my old databases are still there! After roughly 6 purges/removals, and erasers of /etc/mysql contents, all my data is still there. I wonder where that info is stored. I guess I should be glad, but when things happen that dont seem logical like that, I get irritated. Why not remove all traces of the application when the user chooses to 'purge'?

Thanks for all your help everyone

---

### Post by mlind on 2007-05-14
Debian's/Ubuntu's database stuff is probably stored under /var/lib (postgresql uses /var/lib/postgresql).

---

### Post by superyounan1 on 2007-05-14
> **mlind said:**
> Debian's/Ubuntu's database stuff is probably stored under /var/lib (postgresql uses /var/lib/postgresql).

yeah, i actually renamed `/var/lib/mysql/mysql` to `mysql-`, and it recreated the original, i thought that would take care of it. But anyway, i doubt this will happen again any time soon, most likely an isolated case.

---

### Post by mckooiker on 2007-12-22
> **cvi said:**
> hello again,

The mysql server starts up from the init scripts, so it will run even if gnome is in safe mode. Regarding the sysmaint problem. I've done that before, it normally happens when I was setting one of the mysql user passwords and forgot to include the 'where' part of the sql statement. :oops: 

Try one of the following to stop the server:
1.sudo  cat /var/run/mysqld/mysqld.pid (it should return the process id of the mysql server if its running) 
Then type 'sudo kill ' and the number you got from the command above

2. Type ps ax and look for the process id of the mysql server. Then type 'kill ' and the process # from the first column.


Then try one of the apt-get commands to reinstall /remove etc.

If it still won't complete, you can try 

dpkg --remove mysql-server


When the computer was running the filesystem check, did it run a short check (a couple of minutes or less) or was it a full filesystem check?

Hope it helps

Thanks a lot. I had a problem with a mysql5.0 update, but didn't manage. After killing the mysql server (step 1) I managed to do the update normally.

P.S.: wouldn't it be easier to add | grep mysql to the command if you're looking for the mysql processes?

---

