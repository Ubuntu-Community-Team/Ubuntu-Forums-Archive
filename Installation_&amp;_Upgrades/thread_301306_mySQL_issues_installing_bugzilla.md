---
title: "mySQL issues installing bugzilla"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by david3d on 2006-11-16
I'm trying to install bugzilla but it's failing to create the proper databases.

It appears as though the dpkg-reconfigure part of the install process is trying to use 'root'@'localhost' rather than debian-sys-maint account to install the database and is failing b/c dpkg doesn't know the proper password for the local root mysql account.

Anyone know how to get mySQL and apt-get and dpkg-reconfigure to install packages that need databases setup smoothly?

--
David Miller

---

### Post by adamkane on 2006-11-17
I presume this is what you need:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by david3d on 2006-11-17
Thanks for the suggestions Adam but I guess my original post wasn't clear enough as to what my problem is.  

  My problem/question is why is apt-get failing to install databases for programs that require them?  

  The error that I'm getting is in the dpkg-reconfigure stage of the install where the ncurses dialog boxes present you with a series of questions and then attempts to create the database based on your answers.  At that point I'm getting an error message saying that it failed to create the database due to login error using 'root'@'localhost' password(YES).  Or something along those lines.  If I look at the /etc/dbconfig-common/bugzilla.conf file it's showing that debian-sys-maint@localhost should be the account being used to create the databases so I'm a bit perplexed as to why I'm running into this problem or how to solve it.

  I ran into this problem when I installed Mythtv as well.  But in that case I have a fair amount of experience with mythtv under other distros and worked around the problem.  Now I'm trying to install bugzilla and again apt-get fails to create the database.  Unfortunately, in this case I don't know enough about bugzilla to pick up the pieces from where apt-get left the install.

--
David

---

### Post by david3d on 2006-11-17
Adam,
  Now that I've re-read your post I noticed the last 2 lines.  Are you saying that I need to leave the 'root'@'localhost' account with a blank password in order for apt-get to setup databases properly or that the default root@localhost password for mysql is <blank>?    I'm not that new to Linux or mysql...but I am new to the Ubuntu/debian way of doing things.  The first thing I did after installing mySQL was to log into mysql and set a proper password for both root accounts in mySQL user table.  Is that what cause my problem?
--
David

---

### Post by adamkane on 2006-11-17
Correct. Don't change any passwords, until you've successfully accessed mysql through phpmyadmin. That way you know whether you have a working installation.
 
I haven't tested bugzilla, so I don't know your specifics yet.

---

