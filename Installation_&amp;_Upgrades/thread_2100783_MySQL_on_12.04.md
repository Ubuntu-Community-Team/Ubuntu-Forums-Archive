---
title: "MySQL on 12.04"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by Lagbehind on 2013-01-02
I am new to Ubuntu and have been trying to install mysql on to a laptop.  A laptop which I bought specifically to learn about Ubuntu.  

Is there an idots step by step guide I can use since I seem to have created a user called mysql and I am really confused about the issue of not being able to access the root password in ubuntu. I assume it is not needed for the root of mysql is it the same different?

How do I run a client to access the database any pointers please?



_**So far**_

I think I have installed mysql, it's not a good start is it?  On the command line (as user rd) I tried:

                                  [FONT=Ubuntu][SIZE=2]**sudo apt-get install mysql-server**[/SIZE][/FONT]
  
                                    rd@rd-W240HU-W250HUQ:~$ sudo apt-get install mysql-server
[sudo] password for rd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb libboost-date-time1.46.1 libmusicbrainz4c2a libvpx0
  libgrail1 amarok-help-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

and then 

rd@rd-W240HU-W250HUQ:~$ sudo netstat -tap | grep mysql
tcp        0      0 localhost:mysql         *:*                     LISTEN      1090/mysqld     

So assume it must be running?.

---

### Post by The Cog on 2013-01-02
Yes it's running. 
But it's only listening on the loopback address at the moment. If you want it to listen for connections from other boxes, you will need to edit a text file somewhere, perhaps /etc/mysql.conf or something like that, then restart the service.

There is a text mode client that you start with a command like
```
mysql -u root -p
```
which tries to log in to the local mysql a user root. Mysql has its own user database so root here is not the same thing as the Linux root account, it the the name of the mysql administrator account.

There is also a GUI mysql application called mysql-workbench. The package to install for this GUI client is also called mysql-workbench.

---

### Post by Lagbehind on 2013-01-02
Thank you that's very useful.  I will in due course want to link to another box etc. but for the moment I just want to try to do what I have done in ms-win os.  Thanks for the information about workbench that was going to be one of my next questions..

Thanks again

---

### Post by Lagbehind on 2013-01-02
Can I be really lazy and ask can you point me to some easy instructions to install workbench?

---

### Post by The Cog on 2013-01-03
```
sudo apt-get install mysql-workbench
```should do the trick.

---

### Post by Lagbehind on 2013-01-03
Thanks - I have downloaded it it has installed.  I assume that it will configure to 127.0.0.1:3306?

---

### Post by The Cog on 2013-01-04
I think it installs with localhost in the host list by default. For other hosts, click New Connection and enter the name/address and port.

---

### Post by Lagbehind on 2013-01-06
Thanks very much.

---

### Post by Lagbehind on 2013-01-06
A couple more questions not directly related but relevant:

1. How do I install php to work on a single pc is it as straight forward as Mysql and workbench?

2. I understand there is a Libreoffice equivalent to the MS-Access database (which did not install when I installed it) how do I install this software?

---

### Post by The Cog on 2013-01-07
1: I hve no idea

2: The package name is libreoffice-base
sudo apt-get install libreoffice-base

It needs a java runtime:
sudo apt-get install openjdk-6-jre

I'm not sure if you will think it's as good as Access. Last time I tried it (a few years ago), I thought it seemed very clunky.

---

### Post by Lagbehind on 2013-01-07
Thanks will look into this.  Not really worried about how clunky, just want to assess the lie of the land so to speak.

---

### Post by SeijiSensei on 2013-01-07
> **Lagbehind said:**
> 1. How do I install php to work on a single pc is it as straight forward as Mysql and workbench?

```
sudo apt-get install php5 libapache2-mod-php5 php5-mysql
```

The second package provides support to push files with .php extensions through the PHP parser.  The third package includes the driver that lets PHP talk to MySQL servers.

The installation is simple, but you'll need to learn how to write PHP code.  

After you have installed PHP, check out the installation by first creating the file /var/www/info.php like this:

```
sudo echo '<?php phpinfo()?>' > /var/www/info.php
```

Then visit [http://localhost/info.php](http://localhost/info.php) with a browser.  You should see a complete listing of PHP and its installed modules and services.

---

