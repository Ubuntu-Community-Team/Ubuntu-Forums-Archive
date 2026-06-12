---
title: "PHP cannot access mySQL"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by gblake on 2008-07-24
Hi

This is my first thread here, I'm new to Ubuntu and relatively new to Apache. I guess there are probably a huge number of threads about this topic but I couldn't find my specific problem. Apologies if there's a more appropriate section to post this.

I've installed Apache, PHP5 and mySQL on Ubuntu 8.04 and all seemed ok at first. However I wanted to get a Content Management System (CMS) installed and it was when I was configuring it that I realised that the PHP functions that are used to access mySQL were not working. It was reporting an error, "call to undefined function mysql_connect()". I then discovered that my phpinfo page had no mention of mySQL.

Using this forum I've tracked down the mysql.so file and my php.ini file has a reference to it but still no luck, even after an apache restart.

Any advice / help would be welcome.

Thanks

---

### Post by ad_267 on 2008-07-24
I found this explained easily how to install apache, php and mysql: [http://howtoforge.com/ubuntu_lamp_for_newbies](http://howtoforge.com/ubuntu_lamp_for_newbies)

I think you need to install php5-mysql

---

### Post by Darkade on 2008-07-24
yep install php5-mysql
```
sudo apt-get install php5-mysql
```

---

### Post by gblake on 2008-07-25
Ah, thankyou for your help.

I'm not sure exactly what the problem but I followed the steps at the [**http://howtoforge.com/ubuntu_lamp_for_newbies**]("http://howtoforge.com/ubuntu_lamp_for_newbies") site (although mostly it was already set-up) and got it working.

I'd found the original mysql.so file that I was using in a perl5 folder. After I'd tried some of the installation steps the 'locate mysql.so' threw up some new versions, one of which was in a php5 folder. I copied that to my **/usr/lib/php5/ext** folder (over-writing the old version), restarted apache and that did the trick.

Excellent! Thankyou!

---

### Post by Darkade on 2008-07-25
LOL, yep, that should do the trick, however installing php5-mysql does the same thing :P:P LOL

Glad you solved it

---

### Post by absorb on 2009-07-20
try this, actually we have the same problem but it is working now..
hope it help you with this..
[root mode]
[installing]
1. installing apache 2
   apt-get install apache2

2. installing php 5
   apt-get install php5

3. install Apache MySQL module and bundle MySQL to PHP
   apt-get install libapache2-mod-auth-mysql php5-mysql

after you finished try it first.
if it's not working try configure the apache2 and php5

[configuring apache2 and php5]
1.   nano /etc/apache2/apache2.conf
2.   then add the following code after ServerRoot "/etc/apache2"
    ServerName "localhost"

    so it look like this
    ServerRoot "/etc/apache2"
    ServerName "localhost"

3.  nano /etc/php5/apache2/php.ini
4.  then go to Dynamic Extensions
    find this
    ;extension=msql.so
    then uncomment and change extension=msql.so into extension=mysql.so

    so it look like this
    extension=mysql.so
 
5.  then the last part is restart your apache
    /etc/init.d/apache2 restart

---

