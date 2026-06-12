---
title: "Downgrading MySql from 5 to 4.1 in Dapper"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by dlamers on 2006-06-05
I've recently installed Ubuntu 6.06 to host a specific application.  After much searching on the web and this forum, I discovered that the application does not work under MySql 5 and I need to downgrade to MySql 4.1.  I removed version 5 and used the command 'apt-get install mysql-server-4.1' which I found in this forum.  This is the message that I receive:

[I]reading package lists... Done
Building dependency tree... Done
Note, selecting mysql-server-5.0 instead of mysql-server-4.1[/I]

How can I force apt-get to install version 4.1 rather than 5.0?  I've tried to download the 4.1 binary, but then I run into dependancy he!!

Thanks in advance
Dan

---

### Post by ubnoobie on 2006-06-05
use aptitude. it will allow you to visualize the problems.. installed packages dependant on version 5 (if any) and any conflicts with installing version 4.1...

---

### Post by dlamers on 2006-06-05
Thanks,
I tried this "aptitude install mysql-server-4.1" and received this error.  Note that I only made it this far after changing my /etc/apt/sources.list to use "deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe"

Unpacking mysql-server-4.1 (from .../mysql-server-4.1_4.1.15-1ubuntu5_i386.deb) ...
Aborting downgrade from (at least) 5.0 to 4.1.
dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

I think I'm getting further, but I have no idea where to go from here.

---

### Post by ubnoobie on 2006-06-05
i'm sorry.. by "use aptitude" i meant to use it interactively. just use "sudo aptitude"

---

### Post by adamkane on 2006-06-07
Best to avoid mysql 4.1 on ubuntu. Choose mysql 4.0 or mysql 5.0:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by dmartin on 2006-06-11
I'm having the same problem trying to downgrade to mysql 4, after dapper upgraded me to Mysql 5.  And I'm sorry to say, but you are wrong - Dapper's "mysql-server" is pointing at mysql 5.  And when you try to install 4 using "apt-get install mysql-server-4.1", you end up with the error described above - dpkg fails to downgrade without much of an explanation.

The reason I am trying to downgrade is really a bug.  The dapper version of Mythtv is .18x, but the database won't populate because of a new reserved word on Mysql 5.  It's fixed in Mythtv .19, but since dapper packages .18, it's impossible to get Mythtv installed on Dapper because you can't downgrade to Mysql 4.1 if you have Mysql 5.

---

### Post by dmartin on 2006-06-11
Ahah, I figured it out.  If you delete or move /var/lib/mysql, you can downgrade to 4.1.  In other words, it won't downgrade since you have databases that were in mysql 5 format, and by removing the databases you can downgrade.

---

### Post by recover89 on 2006-06-14
In other words, you have to mark mysql-server for COMPLETE REMOVAL in synaptic.

---

### Post by Stusy on 2007-07-05
I'm having a very similar problem to the above....

I've been a fedora user for some time. I've installed the Ubuntu 6 server lamp

We have an server running, Apache, Tomcat and MYSQL with the relevant connectors. I've got a test system running on Ubuntu however the MySql version is causing problems with the Java applications being served by Tomcat.

Its been tested and at this current time the Java app only supports version 4.x

I've basically been trying the code in the posts with loads of different options, but it comes back to that fact that its reporting that:-

Package mysql-server-4.1 is a virtual package provided by:
  mysql-server-5.0 5.0.22-0ubuntu6.06

so whenever I install 4.1 it always 5.0


general code I've been running:-

```
/etc/apt/sources.list
added
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe

cd /etc/init.d

./mysql stop

sudo apt-get remove mysql-server-5*

sudo apt-get remove --purge mysql-server-5*

rm -rf /var/lib/mysql

sudo apt-get install apache2 php5 mysql-client mysql-server libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

or 

sudo apt-get install mysql-server-4.1

```

No i'm starting to get a bit fed up with it....

By the way Hi

---

### Post by Stusy on 2007-07-06
Stuff it.

Started with a blank install and not teh lamp instalation and that worked first time.....

---

### Post by LaVache on 2007-07-26
This same problem plagued me when I needed to downgrade but I got through it.  

I was getting the same error as Stusy:
[I]Package mysql-server-4.1 is a virtual package provided by:
mysql-server-5.0 5.0.22-0ubuntu6.06[/I]

I had already removed mysql:
**sudo apt-get remove mysql-client-5.0**

which removed both mysql client and server packages.

I had also manually removed **/var/lib/mysql**

BUT!!!  I was able to get around this by first editing **/etc/apt/sources.list** to enable the universe and multiverse respositories.  

Next I ran **sudo apt-get update**

Then I again tried to install mysql-server-4.1 and this time with success:
**sudo apt-get install mysql-server-4.1**

Hope this helps someone

---

