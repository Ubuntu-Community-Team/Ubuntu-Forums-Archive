---
title: "When to use Ubuntu 6.06 Alternate Install Disk."
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by jlr4u on 2007-01-01
I just went through loading Ubuntu 6.10 on a new machine that I am building and have plans on using it as a PVR with Myth TV.  I struggled getting a non-supported Dlink wireless card working,  We loaded Ndiswrapper, Nvidia Drivers, and  IVTV for the Hauppauge PVR-500 tuner.   I was even able to record and playback from Terminal commands.

Now that I wanted to install Myth-TV, I started loading it from the Gui using the Synaptic Package Manager. (Big mistake :( ). I have hosed up everything, because MySQL was not loaded first and I can't get through MySQL passwords.

After reading  :
[http://https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend#head-efc7a1a32622b1ba4359ea774469c0a5fc97ee74]("http://https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend#head-efc7a1a32622b1ba4359ea774469c0a5fc97ee74")

It talks about using the 6.06 alternate install disk.  I am thinking about staring over from scratch and trying out the 6.06 version instead of trying to figure out how to repair my 6.10 version which took a week to learn the load process.  I am not afraid to start over, I will learn, and that's a good thing.   

My son started loading Ubuntu 6.10 on a system he built and ran into similar issues with the NVIDIA drivers and graphics. 

Reference :
[http://www.ubuntuforums.org/showthread.php?t=324414&highlight=Alternate+Install+Disk]("http://www.ubuntuforums.org/showthread.php?t=324414&highlight=Alternate+Install+Disk")

So when should one use the alternate 6.06 CD instead of the 6.10 version?

---

### Post by wpshooter on 2007-01-01
I would always try the DESKTOP (live) CD version of either Dapper 6.06.1 or Edgy 6.10 before I tried to install with the ALTERNATE CD on either Dapper or Edgy ?  If the DESKTOP version does not work with either one or both, I would then try the ALTERNATE (text based installer).

You probably want to stay with Dapper if you are interested in the long term support feature.

However, I have found Edgy is very stable NOW and I am using that until the next animal comes along.

Good luck.

---

### Post by superm1 on 2007-01-01
> **wpshooter said:**
> I would always try the DESKTOP (live) CD version of either Dapper 6.06.1 or Edgy 6.10 before I tried to install with the ALTERNATE CD on either Dapper or Edgy ?  If the DESKTOP version does not work with either one or both, I would then try the ALTERNATE (text based installer).

You probably want to stay with Dapper if you are interested in the long term support feature.

However, I have found Edgy is very stable NOW and I am using that until the next animal comes along.

Good luck.
The idea with the alternate disk is that you don't need to install everything.  It saves you on space, since you install into a command line system and just what you need on the box beyond that.  There is another guide linked there that will walk you through the process using the ordinary live disk if you'd prefer to have a desktop installed as well.

---

### Post by superm1 on 2007-01-01
> **jlr4u said:**
> I just went through loading Ubuntu 6.10 on a new machine that I am building and have plans on using it as a PVR with Myth TV.  I struggled getting a non-supported Dlink wireless card working,  We loaded Ndiswrapper, Nvidia Drivers, and  IVTV for the Hauppauge PVR-500 tuner.   I was even able to record and playback from Terminal commands.

Now that I wanted to install Myth-TV, I started loading it from the Gui using the Synaptic Package Manager. (Big mistake :( ). I have hosed up everything, because MySQL was not loaded first and I can't get through MySQL passwords.

After reading  :
[http://https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend#head-efc7a1a32622b1ba4359ea774469c0a5fc97ee74](http://https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend#head-efc7a1a32622b1ba4359ea774469c0a5fc97ee74)

It talks about using the 6.06 alternate install disk.  I am thinking about staring over from scratch and trying out the 6.06 version instead of trying to figure out how to repair my 6.10 version which took a week to learn the load process.  I am not afraid to start over, I will learn, and that's a good thing.   

My son started loading Ubuntu 6.10 on a system he built and ran into similar issues with the NVIDIA drivers and graphics. 

Reference :
[http://www.ubuntuforums.org/showthread.php?t=324414&highlight=Alternate+Install+Disk](http://www.ubuntuforums.org/showthread.php?t=324414&highlight=Alternate+Install+Disk)

So when should one use the alternate 6.06 CD instead of the 6.10 version?
Also, if you haven't wiped the box yet - I can help you through the troubles with mysql and such.  Installation from the GUI will work fine, but some people seem to run into password troubles every so often.

---

### Post by jlr4u on 2007-01-02
I would appreciate it if you can walk me through getting MYSQL up and running.  I am having a lot of problems with it and can not seem to get through the password.

```
jlr@JLR-PVR:~$ sudo grep DBPassword /etc/mythtv/mysql.txt
Password:
DBPassword=mypwhere
```

If I try the following:
```
mysqladmin -u root password ‘mypwhere'
or
 mysqladmin -u root password ‘anything'
```

The screen returns a '>" greater than sign and I must press <ctrl> + 'C' to escape

```
jlr@JLR-PVR:~$ locate mc.sql
[COLOR="Blue"]**/usr/share/mythtv/sql/mc.sq**[/COLOR]l
```

```
jlr@JLR-PVR:~$ sudo /etc/init.d/mysql restart
Password:
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [ ok ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
jlr@JLR-PVR:~$
```

I don't know what the password is for mysql or how to start it.
I don't know what the password is for root
.
When they talk about root password, are they referring to the Linux root user, or the MySQL root user?

Under System - Administration  -users and groups:
Users:
     I only have root and my own user account (only 2)
Manage Groups:
      I see mythtv and mysql along with many others.

 Please help!

---

### Post by superm1 on 2007-01-02
> **jlr4u said:**
> I would appreciate it if you can walk me through getting MYSQL up and running.  I am having a lot of problems with it and can not seem to get through the password.

```
jlr@JLR-PVR:~$ sudo grep DBPassword /etc/mythtv/mysql.txt
Password:
DBPassword=mypwhere
```If I try the following:
```
mysqladmin -u root password ‘mypwhere'
or
 mysqladmin -u root password ‘anything'
```The screen returns a '>" greater than sign and I must press <ctrl> + 'C' to escape

```
jlr@JLR-PVR:~$ locate mc.sql
[COLOR=Blue]**/usr/share/mythtv/sql/mc.sq**[/COLOR]l
``````
jlr@JLR-PVR:~$ sudo /etc/init.d/mysql restart
Password:
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [ ok ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
jlr@JLR-PVR:~$
```I don't know what the password is for mysql or how to start it.
I don't know what the password is for root
.
When they talk about root password, are they referring to the Linux root user, or the MySQL root user?

Under System - Administration  -users and groups:
Users:
     I only have root and my own user account (only 2)
Manage Groups:
      I see mythtv and mysql along with many others.

 Please help!
Okay.  You don't want to use the mysqladmin tool.  What you will want to do is login with the ordinary mysql tool.

Attempt to login:
```
mysql -u root mysql
```
Unless you changed your root password for mysql, there is no password by default.

Now issue this command to reset the mythtv password to the password stored in /etc/mythtv/mysql.txt:```

UPDATE user SET Password=PASSWORD('mypwhere') WHERE user='mythtv';
FLUSH PRIVILEGES;
```

Also, copy your mysql.txt to your .mythtv directory.  This will make sure that things get properly set up with passwords the first time around.
```
sudo cp /etc/mythtv/mysql.txt ~/.mythtv/mysql.txt
sudo chown USER:GROUP ~/.mythtv/mysql.txt
```
where USER is your username and
where GROUP is your groupname.

---

### Post by jlr4u on 2007-01-02
The problem is that I must have set the password and don't know what it is,
```
jlr@JLR-PVR:~$ mysql -u root mysql 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

I have tried the same command with the  -p and can not figure out what I set it to.

---

### Post by superm1 on 2007-01-02
> **jlr4u said:**
> The problem is that I must have set the password and don't know what it is,
```
jlr@JLR-PVR:~$ mysql -u root mysql 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```I have tried the same command with the  -p and can not figure out what I set it to.
Well this being the case, 
you can try to remove mysql-server and choose the setting in symatic to remove all configuration files from apt.  Remove /var/lib/mysql if its still there and anything in /etc/mysql.

Hopefully this will take out the mysql server, all settings, users, passwords etc.

Reinstall mysql-server and mythtv-database.  Hopefully you will be able to login with the root user now.

---

### Post by jlr4u on 2007-01-03
Sorry I did not get back to you .   I tried your suggestion, but it gave me various errors trying to remove mysql-server with messages about dependencies with MythTV.    I decided to bite the bullet and reload from scratch.  I even did a new partition.

My system is now up with all the hardware working.   I have not loaded MySQL or started MythTV.  What is the best procedure for me to follow now that I have a clean load.   Should I install MYSQL first?   Should the install be through terminal commands, or just use Synaptic?

Thank You for your support!:)

---

### Post by superm1 on 2007-01-03
> **jlr4u said:**
> Sorry I did not get back to you .   I tried your suggestion, but it gave me various errors trying to remove mysql-server with messages about dependencies with MythTV.    I decided to bite the bullet and reload from scratch.  I even did a new partition.

My system is now up with all the hardware working.   I have not loaded MySQL or started MythTV.  What is the best procedure for me to follow now that I have a clean load.   Should I install MYSQL first?   Should the install be through terminal commands, or just use Synaptic?

Thank You for your support!:)
Follow through the steps on the help.ubuntu.com pages for a backend/frontend/desktop starting at the mythtv installation.  They will walk you through using synaptic and things *should* go well :)

---

### Post by jlr4u on 2007-01-05
I reloaded MySQL and MythTV from the help site, and things went a little better this time.  I was able to scan the TV channels in the mythtv-setup, but I still am having problems gettting MythTV to run and I believe it is again related to the MySQL setup and permissions.  I was careful not to enter any password for MySQL and issued the command  mysql -u root mysql

```
 mysql -u root mysql
```
This returns a mysql> prompt
I then used your suggestion with the following code:

```
mysql> UPDATE user SET Password=PASSWORD('newpwhere') WHERE user='mythtv';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 2  [COLOR="Red"]**Changed: 0**[/COLOR]  Warnings: 0
```

I was afraid to continue because no rows were updated.
I also used the following command for the correct Passsword in the previous code and of course the password changed after reloading.
```
sudo grep DBPassword /etc/mythtv/mysql.txt
```

Can you put me back on track and tell me why the command updated 0 rows?

---

### Post by kebes on 2007-01-05
Even though it says "0 rows affected" you can quickly check whether or not the password update worked. Just try:
```

mysql -u mythtv

```
If you get into mysql without entering the password, then something is wrong! If it denies access, then that's a good thing, and you can go:
```

mysql -u mythtv -p

```
(and then type in the password) If you get into mysql this time, then that means it worked and the password is set properly.


P.S.: You did create a user "mythtv" before trying to change the password for that user, right? (Or perhaps the MythTV script did that?)

---

### Post by jlr4u on 2007-01-05
YEH - That worked fine and I am able to log in using
```
mysql -u mythtv -p
```
And enter the PW.

I did not issue the 
```
FLUSH PRIVILEGES;
```

OR
```

sudo cp /etc/mythtv/mysql.txt ~/.mythtv/mysql.txt 
sudo chown USER:GROUP ~/.mythtv/mysql.tx
```t

So I guess I need to do that --- and then what?

---

### Post by kebes on 2007-01-05
> **jlr4u said:**
> So I guess I need to do that --- and then what?

Can you re-summarise what your situation is and what your remaining problems are?

As I understand it, you're following [this guide]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend#head-efc7a1a32622b1ba4359ea774469c0a5fc97ee74") about installing MythTV. Is that correct? What step have you gotten to?

What works and what doesn't work?

---

### Post by jlr4u on 2007-01-05
Well, I went through the sudo mythtv-setup and in the general area where it asked for the IP address, I was not sure what to use, so I used my IP address found in my interfaces table and used that,   I went though the set up and was even able to watch the scan pull in the channels.  When I exited from that and  did the following.

jlr@JLR-PVR:~$ sudo /etc/cron.daily/mythtv-backend
Password:
```
[COLOR="Red"]**Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed**[/COLOR]
--19:32:22--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... **[COLOR="Red"]401 Unauthorized[/COLOR]**
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:22--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:23--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:23--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:23--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:24--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:24--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:25--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:25--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:25--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:26--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:26--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:27--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:27--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.


```

It looks like i have two problems.  
1.  it does not appear to be connecting to the database to do the updates.
2.  Problem with the zap2it.    Perhaps I did not set that up properly

Now that I issued the password change for mytv. I think I have to complete the commands listed in my previous email first

---

### Post by kebes on 2007-01-05
(Note: I setup my mythTV a few years ago... some of the commands/procedures may have changed... Let me know if something I say doesn't make sense.)

Yes you should complete the commands you listed before. Then go back into mythtvsetup and double-check the settings you have for zap2it. However you may aswell also try going into mythtv (start mythtvbackend and then mythtvfrontend) and seeing if the channel listing appears or not.

---

### Post by jlr4u on 2007-01-06
When I went through the procedure and tried to start the backend, I received the following error.

sudo /etc/init.d/mythtv-backend restart

Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

---

### Post by superm1 on 2007-01-06
> **jlr4u said:**
> Well, I went through the sudo mythtv-setup and in the general area where it asked for the IP address, I was not sure what to use, so I used my IP address found in my interfaces table and used that,   I went though the set up and was even able to watch the scan pull in the channels.  When I exited from that and  did the following.

jlr@JLR-PVR:~$ sudo /etc/cron.daily/mythtv-backend
Password:
```
[COLOR=Red]**Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed**[/COLOR]
--19:32:22--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... **[COLOR=Red]401 Unauthorized[/COLOR]**
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:22--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:23--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:23--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:23--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:24--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:24--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:25--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:25--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:25--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:26--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:26--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:27--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
--19:32:27--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.


```It looks like i have two problems.  
1.  it does not appear to be connecting to the database to do the updates.
2.  Problem with the zap2it.    Perhaps I did not set that up properly

Now that I issued the password change for mytv. I think I have to complete the commands listed in my previous email first
Your zap2it information appears to be wrong here (or you don't have a lineup chosen and assigned to an input).  Double check the username and password being used for zap2it under mythtv-setup.

> 
	When I went through the procedure and tried to start the backend, I received the following error.

sudo /etc/init.d/mythtv-backend restart

Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

This isn't necessarily an error, it's related to using sudo to start the backend.  Check and see that the backend process is running afterwords.
Check /var/log/mythtv/mythbackend.log for any real error messages.

---

### Post by jlr4u on 2007-01-07
I still am having problems.   At one time, I was able to open the front end and watch TV and change channels,  but I have always had a problem with the channel list even after updating the zap2it info.  I have changes something and now I can't seem to get the backend up at all.  I went over and over the commands you sent which got  me started in the right direction.  I believe one of the commands I set incorrectly because I do not fully understand it.
sudo chown USER:GROUP ~/.mythtv/mysql.txt
where USER is your username and
where GROUP is your groupname.

I used **[COLOR="Red"]root[/COLOR]** for the group and issued the command.

```
sudo chown jlr:**[COLOR="Red"]root[/COLOR]** ~/.mythtv/mysql.txt
```

I think this is not what I wanted, but my user name is in many groups, so I am confused.   I issued the following command that may help.
```
jlr@jlr-PVR:~$ sudo grep jlr /etc/group 
adm:x:4:jlr
dialout:x:20:cupsys,jlr
cdrom:x:24:haldaemon,jlr
floppy:x:25:haldaemon,jlr
audio:x:29:jlr,mythtv
dip:x:30:jlr
video:x:44:jlr,mythtv
plugdev:x:46:haldaemon,jerry
lpadmin:x:109:jlr
scanner:x:111:cupsys,hplip,jlr
jlr:x:1000:
admin:x:114:jlr
mythtv:x:116:jlr
```
I am just guessing that the correct group would be adm, admin, or mythtv, but can you explain.

---

### Post by kebes on 2007-01-07
Unless you are doing something 'fancy' then the group is the same as the user. For instance if you list all the files in your home directory:
ls -laF ~/

You will see lines like:
drwx------  2 kebes kebes    4096 2007-01-06 19:20 .aptitude/
-rw-------  1 kebes kebes    7122 2007-01-07 12:29 .bash_history

Notice that for me they say "kebes kebes" (for you they probably say "jlr jlr" or whatever). The first one refers to the user, the second one to the group. Although "jlr" is the member of many groups, typically what you want files owned by "jlr" to just be in the default "jlr" group.

sudo chown jlr:jlr ~/.mythtv/mysql.txt



However I'm not sure if that's the source of your problems... As I understand it, you're following this guide:
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

What step are you at? You say that the backend doesn't start... so when you go:

sudo /etc/init.d/mythtv-backend start

And then go:

pgrep mythtv -l

Do you get anything listed? 


Also... what does the logfile say:
more /var/log/mythtv/mythbackend.log

---

