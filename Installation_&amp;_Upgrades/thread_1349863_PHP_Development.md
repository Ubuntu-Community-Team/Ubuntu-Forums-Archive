---
title: "PHP Development"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Ciwan on 2009-12-08
Hello Guys

After doing some Research I found out that in order to do PHP Development on Ubuntu I would need to type the following in a terminal:


```
sudo apt-get install php5 mysql-server apache2 phpmyadmin
```

I have done that. But now I do not know how to start the System, also where the [ public_html ] folder is !!

I would greatly appreciate any help with this.

Thank You.

---

### Post by H4F on 2009-12-08
your web server folder is at /var/www
you can access phpmyadmin at [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
note that you will have to change the permission of your php script to make them runnalbe I guess.

---

### Post by m_duck on 2009-12-08
> **H4F said:**
> note that you will have to change the permission of your php script to make them runnalbe I guess.
I don't think a permission change is necessary. As long as the .php files are in /var/www or some subdirectory thereof, they will be executed when called by the server? I don't remember having to change their permissions before, but I've not tried for quite a while.

---

### Post by dharanitharan on 2010-01-12
I started the apache server. It shows It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

but when i try to start phpmyadmin i got the following message:
The requested URL /phpmyadmin was not found on this server.

I already installed the phpmyadmin using sudo apt-get install phpmyadmin

---

### Post by phillw on 2010-01-12
Hi, from your browser ..

type in    [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)   Or, just click on the link, if you're feeling lazy ;)

That should fire phpmyadmin up for you.

Regards,

Phill.

---

### Post by dharanitharan on 2010-01-12
this time also i got the same message only

---

### Post by phillw on 2010-01-12
Hmmm..

Can you go into System --> Administration --> Synaptics Package Manager

Then type in phpmyadmin in the search window and see if you have a little green square next to the entry for phpmyadmin

Thanks,

Phill.

---

### Post by dharanitharan on 2010-01-12
Ya, i ve that green filled square

---

### Post by Maheriano on 2010-01-12
It'd probably be easier to just get cheap hosting somewhere else for $5 a month.

---

### Post by phillw on 2010-01-12
Hmmm....

```
 ps -ef | grep apache 
```

Should be about 10 entries

```
 ps -ef | grep mysql
```

Should have a line starting with mysql and ending with  /usr/sbin/mysqld

Phill.

---

### Post by dharanitharan on 2010-01-12
> **phillw said:**
> Hmmm....

```
 ps -ef | grep apache 
```

Should be about 10 entries

```
 ps -ef | grep mysql
```

Should have a line starting with mysql and ending with  /usr/sbin/mysqld

Phill.
i got the following message

dharani@dharani-desktop:~$ ps -ef | grep apache
root     21968     1  0 03:16 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21977 21968  0 03:16 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21978 21968  0 03:16 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21979 21968  0 03:16 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21980 21968  0 03:16 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21981 21968  0 03:16 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 22355 21968  0 03:16 ?        00:00:00 /usr/sbin/apache2 -k start
dharani  31011 30991  0 04:29 pts/0    00:00:00 grep --color=auto apache
dharani@dharani-desktop:~$ ps -ef | grep mysql
root      4823     1  0 Jan12 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     4931  4823  0 Jan12 ?        00:00:08 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      4933  4823  0 Jan12 ?        00:00:00 logger -t mysqld -p daemon.error
dharani  31014 30991  0 04:30 pts/0    00:00:00 grep --color=auto mysql

---

### Post by phillw on 2010-01-12
> **Maheriano said:**
> It'd probably be easier to just get cheap hosting somewhere else for $5 a month.

Yikes !!! - that much ?!!

My Lamp server costs me, errr.... $0.00 / month :D

I even let it 'out to play' running a forum & website.

Plus, i learned much more by breaking it than i would on a hosting package ;)

Phill.

---

### Post by dharanitharan on 2010-01-12
> **phillw said:**
> Yikes !!! - that much ?!!

My Lamp server costs me, errr.... $0.00 / month :D

I even let it 'out to play' running a forum & website.

Plus, i learned much more by breaking it than i would on a hosting package ;)

Phill.
Nice reply to Maheriano, phillw

---

### Post by phillw on 2010-01-12
It appears you're running mysql in safe mode ?

```
sudo stop mysql

```

wait 10 seconds, then
```
sudo start mysql
```

then do the ```
ps -ef | grep mysql
``` again

Phill.

---

### Post by phillw on 2010-01-12
> **dharanitharan said:**
> Nice reply to Maheriano, phillw

We learn more this way - I've no idea where you went wrong - but, we'll find it :)

Phill.

---

### Post by dharanitharan on 2010-01-12
i got the following message:

dharani@dharani-desktop:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                                                                                [ OK ] 
dharani@dharani-desktop:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                                                                                [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
dharani@dharani-desktop:~$ sudo /etc/init.d/mysql status
 * /usr/bin/mysqladmin  Ver 8.42 Distrib 5.1.37, for debian-linux-gnu on i486
Copyright 2000-2008 MySQL AB, 2008 Sun Microsystems, Inc.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version		5.1.37-1ubuntu5
Protocol version	10
Connection		Localhost via UNIX socket
UNIX socket		/var/run/mysqld/mysqld.sock
Uptime:			13 sec

Threads: 1  Questions: 124  Slow queries: 0  Opens: 131  Flush tables: 1  Open tables: 31  Queries per second avg: 9.538
dharani@dharani-desktop:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                                                [ OK ] 
 * Starting MySQL database server mysqld                                                                                                [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

wat to do now

---

### Post by phillw on 2010-01-12
I suspect you have not got all the packages you need.

There is a much easier way to install LAMP, but I don't know if it will work on a part finished install. Let's see if we can finish the install.

```
 sudo apt-get mysql-client 
```Then

```
sudo apt-get libapache2-mod-php5 
```Then ...

```
 gksudo gedit /var/www/info.php
```into that put > 

<?php
phpinfo();
?>and save it

Then ...

```
sudo apt-get php5-mysql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap
php5-mcrypt php5-memcache php5-mhash php5-ming php5-ps php5-pspell
php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl php5-json
```Don't worry if it cannot find them all - that's a long list !!

To put them into you terminal, highlight the entire contents in the code box, then Ctrl-C, then in you terminal SHIFT-Ctrl-V to paste them


Then

```
/etc/init.d/apache2 restart 
```  Then into your browser type [http://localhost/info.php](http://localhost/info.php)

You should see the listing of a load of php information, scroll down it all and see if you have a section for MySQL

I'll see you in a bit !!!

Regards,

Phill.
P.S. I only pay $15 / year for my hosting :-)

---

### Post by phillw on 2010-01-12
Hi,
well, it is bed time for me - approaching 01:00 here in the U.K.

Hoping that the final install part went well. 

A couple of notes .. if the apt-get php5-mysql ...........  line failed & just refused to work, then use this

```
 
aptitude install php5-mysql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-mhash php5-ming php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl php5-json 
```
aptitude is supposed to be being phased out, but on my 10.04 system, apt-get wouldn't work, yet aptitude did. (10.04 is still a trial system, so I expect the odd glitch)


If you still cannot get into phpmyadmin, then the only thing I can think of is that you answered a question wrongly when installing it.


Go into System --> Administration --> Synaptic Package Mananger
type in phpmyadmin - then right click on the green square & choose "Mark for Complete Removal" - then apply the change.


Close Synaptic, drop back into terminal and 



```
apt-get phpmyadmin
```
You will be asked 2 questions ...

[LIST=1]
[*]Web server to reconfigure automatically: **[COLOR=Red]<-- apache2[/COLOR]**
[*]   Configure database for phpmyadmin with dbconfig-common? **[COLOR=Red]<-- No[/COLOR]**
[/LIST]
[COLOR=Black]After that, re-boot your machine.

When restarts, you should be able to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

I'm going to subscribe to this thread, so please leave how you get on & if you are still having a problem.

I'm pretty sure that it will all now work, if it does, please use the "Thread Tools" to mark it as solved.

If it does not - We'll do a re-install of LAMP from the beginning, the correct & easy way.

I'll pick up the email from here tomorrow.

Regards,

Phill.
[/COLOR]

---

### Post by dharanitharan on 2010-01-13
surely phill lets experiment now.. Im going to do wat u ve told

---

### Post by dharanitharan on 2010-01-13
> **phillw said:**
> I suspect you have not got all the packages you need.

There is a much easier way to install LAMP, but I don't know if it will work on a part finished install. Let's see if we can finish the install.

```
 sudo apt-get mysql-client 
```Then

```
sudo apt-get libapache2-mod-php5 
```Then ...

```
 gksudo gedit /var/www/info.php
```into that put and save it

Then ...

```
sudo apt-get php5-mysql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap
php5-mcrypt php5-memcache php5-mhash php5-ming php5-ps php5-pspell
php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl php5-json
```Don't worry if it cannot find them all - that's a long list !!

To put them into you terminal, highlight the entire contents in the code box, then Ctrl-C, then in you terminal SHIFT-Ctrl-V to paste them


Then

```
/etc/init.d/apache2 restart 
```  Then into your browser type [http://localhost/info.php](http://localhost/info.php)

You should see the listing of a load of php information, scroll down it all and see if you have a section for MySQL

I'll see you in a bit !!!

Regards,

Phill.
P.S. I only pay $15 / year for my hosting :-)
This method doesn't work.... I'm going to experiment the next method yu ve told

---

### Post by dharanitharan on 2010-01-13
> **dharanitharan said:**
> This method doesn't work.... I'm going to experiment the next method yu ve told
[http://lacalhost/info.php](http://lacalhost/info.php) wporked well... but i cant open phpmyadmin page

---

### Post by dharanitharan on 2010-01-13
Oops GOD s great phill.... We ve to start from the scratch.. I love this game...

---

### Post by phillw on 2010-01-13
Hi,

Did you mark phpmyadmin up for **complete** removal in Synaptics, apply that change  and then re-install it ?

Phill.

---

### Post by dharanitharan on 2010-01-13
> **phillw said:**
> Hi,

Did you mark phpmyadmin up for **complete** removal in Synaptics, apply that change  and then re-install it ?

Phill.
ya i did like that oly and after that i restarted the machine.. After that also it did not work

---

### Post by phillw on 2010-01-13
Hmm, I'm just reading through a thread with the same problem ... This seemed to fix it ...

```

sudo ln -s /usr/share/phpmyadmin /var/www
```

Try is and let me know how you get on.

Regards,

Phill.

---

### Post by dharanitharan on 2010-01-13
> **phillw said:**
> Hmm, I'm just reading through a thread with the same problem ... This seemed to fix it ...

```

sudo ln -s /usr/share/phpmyadmin /var/www
```

Try is and let me know how you get on.

Regards,

Phill.
whoa... i got it machi... it asking me for username and password.. wat i ve to give now

---

### Post by phillw on 2010-01-13
you need the **root** as the user and the password you gave MySQL when you installed it as the password

Phill.

---

### Post by dharanitharan on 2010-01-13
successfully i logged in machi... But it shows:

The additional features for working with linked tables have been deactivated.. 
when i click that link it shows the following:

$cfg['Servers'][$i]['pmadb'] ... 	not OK 
$cfg['Servers'][$i]['relation'] ... 	not OK 
General relation features: Disabled
 
$cfg['Servers'][$i]['table_info'] ... 	not OK 
Display Features: Disabled
 
$cfg['Servers'][$i]['table_coords'] ... 	not OK 
$cfg['Servers'][$i]['pdf_pages'] ... 	not OK 
Creation of PDFs: Disabled
 
$cfg['Servers'][$i]['column_info'] ... 	not OK 
Displaying Column Comments: Disabled
Bookmarked SQL query: Disabled
Browser transformation: Disabled
 
$cfg['Servers'][$i]['history'] ... 	not OK 
SQL history: Disabled
 
$cfg['Servers'][$i]['designer_coords'] ... 	not OK 
Designer: Disabled

how to enable those things

---

### Post by phillw on 2010-01-13
Sigh ...

go into Synaptics, mark phpmyadmin for complete removal and action that.

Then, still in Synaptics, select phpmyadmin for installation and install it.

Remember, you want to say yes for apache and no to the 2nd question - 

I don't think the apt-get is setting phpmyadmin up correctly on your machine - using sysnaptic should sort that out.

Phill.

---

### Post by dharanitharan on 2010-01-13
Thanks phill. you helped me a lot

---

### Post by phillw on 2010-01-13
Now then ...

The correct way ..

From Ubuntu 9.10 onwards the correct way to install LAMP is..

```
 sudo tasksel
```

Select LAMP and do as it tells you.

Then go into Synaptic and select phpmyadmin

It is **much** easier !!!!

Phill.

---

### Post by AnRkey on 2010-01-21
> **phillw said:**
> Now then ...

The correct way ..

From Ubuntu 9.10 onwards the correct way to install LAMP is..

```
 sudo tasksel
```Select LAMP and do as it tells you.

Then go into Synaptic and select phpmyadmin

It is **much** easier !!!!

Phill.

Wow, that actually worked?!

So how is this different from what I tried?
```
sudo apt-get remove phpmyadmin --purge
sudo apt-get install phpmyadmin
```

---

### Post by AnRkey on 2010-01-21
Oh and thanks chaps ;)

---

### Post by phillw on 2010-01-21
> **AnRkey said:**
> Wow, that actually worked?!

So how is this different from what I tried?
```
sudo apt-get remove phpmyadmin --purge
sudo apt-get install phpmyadmin
```

We tried it, via apt-get - I am assuming that some of the links that phpmyadmin requires to both the PHP & MySQL libraries / locations were not done when we used apt-get. I did a bit of reading & it was the general consensus of opinion that Synaptic works and apt-get some times doesn't.

I used the 'long-way' in 9.04 and it worked okay for me - I'd not tried tasksel in 9.10 as I did an upgrade from 9.04 --> 9.10, but did use it for my 10.04 test rig.

Glad it all worked for you - As of 10.04, the things you can do with tasksel is expanded quite a lot. It is going to make life **so** much easier !!!

Regards,

Phill.

---

