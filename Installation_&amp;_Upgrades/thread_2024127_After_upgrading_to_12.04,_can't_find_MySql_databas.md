---
title: "After upgrading to 12.04, can't find MySql database"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by knhllsn on 2012-07-13
To start with, I'm new to the whole Linux and any and all subsets thereof.

I have one Ubuntu server that I use to run the "FOG" imaging solution for my organization.  I have been using this imaging product for about 2 years and I'm pretty adept at doing what I need to do on this server.  This server is also my DHCP server so I've had to learn some rudimentary understanding of Ubuntu at the command line level, although you would most likely roll your eyes at that statement.  Anyway the platform was built and the "FOG" app. was installed a couple of years ago by someone else.  Until this week, everything was cool beans until I got tired of the Ubuntu upgrade messages and took the plunge to upgrade to v.12.04.  The upgrade ran flawlessly, I thought.  After the upgrade, whenever I attempt to start FOG, I receive an error message stating that it is unable to connect to the DATABASE, root@localhost... PASSWORD=NO.

Help, I've got a 150 PC / 60+ unique images, taking up close to 1TB on the server and I **[SIZE="3"]don't[/SIZE]** want to screw myself up anymore than I already have.  I've poked around some of the folders and used GEDIT to look at a lot of the index.php files as well as a couple of the config.php files.

Thanks for whatever assistance you guys can provide.

---

### Post by The Linuxist on 2012-07-18
Ok, first thing to try is to make sure the MySQL service is even running:

```
sudo /etc/init.d/mysql status
```

and if it's stopped, then run

```
sudo /etc/init.d/mysql start
```

connecting to the MySQL database from the command line:

```
mysql -uroot -p
```

to see if you can connect. If you can get that far, let me know and I'll see what the next steps need to be.

---

### Post by darkod on 2012-07-18
Slight correction:
```
mysql -u root -p
```

It should have a space after -u right?

---

### Post by knhllsn on 2012-07-18
MYSQL -U ROOT -P RETURNS:

enter password:
If I enter a password that I think might be correct, RETURNS:

error 1045 (28000): access denied for user 'root'@'localhost'(using password:_YES_)

If I do not enter a password, RETURNS:


error 1045 (28000): access denied for user 'root'@'localhost'(using password:_NO_)

---

### Post by darkod on 2012-07-18
Note that you need the password for the root mysql user (which is not the same with the root ubuntu user). That password is usually set during mysql installation but can be changed later too.
That is the main user, same like in linux, the root user has maximum permissions.

If you do have another username that you know, and the password, you can try:
mysql -u <username> -p

and enter the password for that user.

Otherwise, it seems you are not entering the correct password for the mysql root user but the mysql server seems to be running after all, otherwise it wouldn't even ask you for a password I guess.

---

### Post by The Linuxist on 2012-07-18
Sounds to me like something has happened to your grant tables upon upgrading. Have you run ```
mysql_upgrade
``` ?

That could help, try it first. Failing that you may need to reset the root password:

[http://www.howtoforge.com/reset-forgotten-mysql-root-password](http://www.howtoforge.com/reset-forgotten-mysql-root-password)

---

