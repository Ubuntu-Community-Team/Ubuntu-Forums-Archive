---
title: "Phpmyadmin installs in version 4.5.4 instead of latest 4.6.4"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by spectatorx on 2016-09-21
I'm setting up lamp on my xubuntu. Lamp works and i can do with it anything i want, now i just do check on components versions. I already have almost everything updated to latest versions, the only exception is phpmyadmin.

I have added ppa:nijel/phpmyadmin to software sources,, updated, installed and at ppa's website i see phpmyadmin available in version 4.6.4 but when i log in to phpmyadmin it is shown as 4.5.4. Also when i try in terminal install again via sudo apt-get install phpmyadmin i get message telling "phpmyadmin is already the newest version (4:4.5.4.1-2ubuntu2).". How can i force-install 4.6.4 from added ppa? I know i could manually install latest version but this is not what i want to achieve, i want to use what ppas were made for: download latest version of software from ppa.

Also i've tried to install via sudo apt-get install phpmyadmin4.6.4 but i get message about no candidate to install which is logical as such package doesn't exist on ppa.


Another interesting thing is i have installed php7.1 RC2 (yes, i set up lamp of latest versions of packages on my own risk as this is not for professional work i do not care, this is for my own purposes, not production use) but in phpmyadmin i see such message: "[COLOR=#444444][FONT=sans-serif]PHP version: 7.0.11-1+deb.sury.org~xenial+1". When i give in terminal "php -v" i get such output: "[/FONT][/COLOR]PHP 7.1.0RC2 (cli) ( NTS )
Copyright (c) 1997-2016 The PHP Group
Zend Engine v3.1.0-dev, Copyright (c) 1998-2016 Zend Technologies
    with Zend OPcache v7.1.0RC2, Copyright (c) 1999-2016, by Zend Technologies"
So i'm sure installed version of php is 7.1 RC2, not 7.0.

---

### Post by howefield on 2016-09-21
> **spectatorx said:**
> I have added ppa:nijel/phpmyadmin to software sources,, updated, installed and at ppa's website i see phpmyadmin available in version 4.6.4 but when i log in to phpmyadmin it is shown as 4.5.4.

Just test installed the package with the PPA and all worked as expected.

What is the output of ...

```
apt-cache policy phpmyadmin
```

---

### Post by spectatorx on 2016-09-21
For some reason when i add ppa address:
ppa:nijel/phpmyadmin
to software sources via gui it works as i said, installs phpmyadmin 4.5.4 but when i added this ppa via terminal with this command:
sudo apt-add-repository ppa:nijel/phpmyadmin
sudo apt-get update
i was able to install phpmyadmin in 4.6.4 version. So i solved my own problem on my own, again xD In phpmyadmin version is displayed now like this: [COLOR=#444444][FONT=sans-serif]Version information: [/FONT][/COLOR][COLOR=#444444][FONT=sans-serif]4.6.4deb1+deb.cihar.com~xenial.1[/FONT][/COLOR]


Anyway, here is output you asked for:
> 
apt-cache policy phpmyadminphpmyadmin:
  Installed: 4:4.6.4+dfsg1-1+deb.cihar.com~xenial.1
  Candidate: 4:4.6.4+dfsg1-1+deb.cihar.com~xenial.1
  Version table:
 *** 4:4.6.4+dfsg1-1+deb.cihar.com~xenial.1 500
        500 [http://ppa.launchpad.net/nijel/phpmyadmin/ubuntu](http://ppa.launchpad.net/nijel/phpmyadmin/ubuntu) xenial/main amd64 Packages
        500 [http://ppa.launchpad.net/nijel/phpmyadmin/ubuntu](http://ppa.launchpad.net/nijel/phpmyadmin/ubuntu) xenial/main i386 Packages
        100 /var/lib/dpkg/status
     4:4.5.4.1-2ubuntu2 500
        500 [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
        500 [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages
     4:4.5.4.1-2ubuntu1 500
        500 [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages




Still, remains just one thing, why phpmyadmin still displays this: [COLOR=#444444][FONT=sans-serif]PHP version: 7.0.11-1+deb.sury.org~xenial+1 instead of 7.1?[/FONT][/COLOR]

---

### Post by howefield on 2016-09-21
> **spectatorx said:**
> For some reason when i add ppa address: ppa:nijel/phpmyadmin to software sources via gui it works as i said, installs phpmyadmin 4.5.4

Both methods work unless there is user error.

No matter, you have the version that you wanted.

> Still, remains just one thing, why phpmyadmin still displays this: PHP version: 7.0.11-1+deb.sury.org~xenial+1 instead of 7.1?

More user error ?

What other PPA have you used ?

---

### Post by spectatorx on 2016-09-21
Here is the whole instruction i created to do all this, now tell me where lies my user error:

> 

Add ppa to software sources:
[noparse]ppa:ondrej/php
ppa:ondrej/apache2[/noparse]


This one ppa add via terminal:
sudo apt-add-repository ppa:nijel/phpmyadmin


sudo apt-get update


sudo apt-get install -f apache2 mysql-server mysql-client php7.1-mysql php7.1-curl php7.1-json php7.1-cgi php7.1 phpmyadmin libapache2-mod-php7.1 php7.1-mbstring php7.1-fpm php7.1-cli php7.1-common php7.1-gd php7.1-bz2 php7.1-xml php7.1-intl php-pear php-imagick php7.1-imap php7.1-mcrypt php-memcache php7.1-pspell php7.1-recode php7.1-sqlite3 php7.1-tidy php7.1-xmlrpc php7.1-xsl php-gettext php-apcu php7.1-zip


To set up phpmyadmin under Apache all you need to do is include at end of file /etc/apache2/apache2.conf the following line:
Include /etc/phpmyadmin/apache.conf


restart apache:
sudo service apache2 reload



---

### Post by AbDk38H on 2016-09-22
You are using php 7.0 for apache (handles php from a web browser) and 7.1 for the client (handles php from the command line). You probably have a directory structure like this:/etc/php/7.0/etc/php/7.0/apache2/etc/php/7.0/cli/etc/php/7.1/etc/php/7.1/apache2/etc/php/7.1/cliIf this is a hobby for you, don't worry too much about it. There are few cases where this might be a problem. I'm having a similar problem currently where I'm running 5.6 with apache but 7.1RC for the command line and it's actually causing issues so I need to figure out how to change the cli version. I'm about to open another ticket for that.

---

### Post by spectatorx on 2016-09-22
Ok, now phpmyadmin displays 7.1.0RC2 version of php. Seems like there were some leftovers after upgrade from 7.0 to 7.1RC2. I removed again 7.1, in command which i mentioned i replaced all 7.1 with 7.0 entries and installed again 7.1. After such purge everything is in latest versions.

/etc/php/ folder you mentioned in my case, even after this lamp reinstall contains 4 folders: 5.5, 5.6, 7.0, 7.1.
5.5 and 5.6 contain only mods-available folder, 7.0 and 7.1 contain few more folders.

Summing it all we can say we have here decent instruction to build lamp with latest components of php, apache, mysql and phpmyadmin.

AbDk38H, i'm not expert on lamp but i think something you want to achieve may be not easy or even impossible. Overall i'm not fan of virtual machines but i think in your case this would be the best solution to set up separate OS as virtual machine and on it setup lamp with php 7.1.

---

