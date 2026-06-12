---
title: "Removing apache2"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by pan69 on 2008-05-30
Hi. I had trouble getting apache up and running the other day. Something was mis configured and I could find out what it was so I decided to start from scratch by removing apache2 and php5 using Synaptic.

This however, does not remove apache2 from my drive. The /etc/apache2 folder is still there with all the config files in it. When reinstalling apache2 ..

> sudo aptitude install apache2 apache2.2-common apache2-mpm-prefork apache2-utils libexpat1 ssl-cert

.. it's not overwriting the config files (like apache2.conf) and reinstalling just ends in another mis configured installation.

If I manually remove the /etc/apache2 folder, then the apache2.conf file is not created so apache won't run. Am I missing or misunderstand something here? I'm not sure what I'm doing wrong...

Any help much appreciated!

Thanks

---

### Post by wdaniels on 2008-05-30
You can use:

```
sudo apt-get purge <package>
```

to delete the config files.

(Or "mark for complete removal" in Synaptic.)

---

### Post by pan69 on 2008-05-30
I've done a:
> sudo apt-get --purge remove apache2
which says it removed apache2 but the /etc/apache2 folder is still there.

Removing apache is not so much the problem. Its actually re-installing it. When I reinstall apache, it fails to create a new /etc/apache2/apache2.conf file. There are no error message when installing though...

where is the /etc/apache2/apache.conf file supposed to come from (I assume the installation should create this)?

---

### Post by wdaniels on 2008-05-30
You can find these things from the [package search]("http://packages.ubuntu.com/search?searchon=contents&keywords=apache2.conf&mode=exactfilename&suite=hardy&arch=any") - apache2.2-common.

---

### Post by pan69 on 2008-05-31
Ah. somehow purging didn't work very well. I tried Synaptic again and was able to completely remove apache2 and php5.

After I reinstall, apache seems to work OK. However, now PHP5 is the culprit. These are the commands I'm using (from [this page](http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5)):

> sudo aptitude install apache2 apache2.2-common apache2-mpm-prefork apache2-utils libexpat1 ssl-cert
> sudo aptitude install libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php5-imagick php5-mcrypt php5-memcache php5-mhash php5-mysql php5-pspell php5-snmp php5-sqlite php5-xmlrpc php5-xsl

When I'm trying to load my *info.php* from localhost it tries to download the file. When I look in the mods-available directory I do not see the *php5.conf* and *php5.load* files, so running *a2enmod php5* results in an error. 

I'm kinda lost at the moment...

---

### Post by js9986 on 2008-06-21
I had the same experience as pan69. I had purged apache2 and php5. Now no matter how much I remove and purge and reload libapache2-mod-php5 I cannot seem to get the /etc/apache2/mods-available/php5.load and /etc/apache2/mods-available/php5.conf files back.

I'm using ubuntu 8.04 desktop version.

/Joe

---

### Post by js9986 on 2008-06-21
This is what I did to get around it:

  cd /tmp
  dpkg -X /var/cache/apt/archives/libapache2-mod-php5_5.2.4-2ubuntu5.1_i386.deb .
  cp ./etc/apache2/mods-available/php5.* /etc/apache2/mods-available
  cd /etc/apache2/mods-enabled
  ln -s /etc/apache2/mods-available/php5.load 
  ln -s /etc/apache2/mods-available/php5.conf
  /etc/init.d/apache2 stop
  /etc/init.d/apache2 start


This made php work in apache. After doing this I went back to the
mods-enabled directory and saw that the php5.load and php5.conf
links were gone, but there is now a link from
/etc/apache2/mods-enabled/cgi.load to
/etc/apache2/mods-available/cgi.load. Even with the php5.load and
php5.conf links now gone from the mods-enabled directory, php still
works in apache2. hmmm.

/Joe  (ubuntu 8.05 desktop)

---

### Post by js9986 on 2008-06-22
CAUTION:

Dont do this as I said above,

cd /tmp
dpkg -X /var/cache/apt/archives/libapache2-mod-php5_5.2.4-2ubuntu5.1_i386.deb .

Note the "." at the end. That is the destination directory and the dpkg statement 
changed the permissions on /tmp from 777 to 755. It messed me up so I could not obtain locks for X or the Synaptic package manager. 

Instead do something like this:

mkdir /tmp/xxx
cd /tmp/xxx
dpkg -X /var/cache/apt/archives/libapache2-mod-php5_5.2.4-2ubuntu5.1_i386.deb .

or just remember to fix up the permissions on /tmp.

---

### Post by vinan on 2009-07-11
after uninstalling apache
try sudo apt-get autoremove

it worked for me

---

### Post by lockit on 2011-06-18
How this is possible ??
I can't remove apache from my server :(
I've also try to reinstall and to remove it again, my server do it without giving me any error all looks fine, but the process still active and use that port(that I want to use for something else), even after reboot... I can change just the port in the apache config, but I don't think is a good solution...

Any Idea ?

I've try with the autoremove as well... no way...

```
Last login: Sat Jun 18 23:29:26 2011 from ***
alex@SMEGPREPGDB01:~$ sudo /etc/init.d/apache2 stop
[sudo] password for alex:
 * Stopping web server apache2                                                  WARNING: MaxClients of 40 exceeds ServerLimit value of 4 servers,
 lowering MaxClients to 4.  To increase, please see the ServerLimit
 directive.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting                                                             [ OK ]
alex@SMEGPREPGDB01:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  WARNING: MaxClients of 40 exceeds ServerLimit value of 4 servers,
 lowering MaxClients to 4.  To increase, please see the ServerLimit
 directive.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]
alex@SMEGPREPGDB01:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server apache2                                                  WARNING: MaxClients of 40 exceeds ServerLimit value of 4 servers,
 lowering MaxClients to 4.  To increase, please see the ServerLimit
 directive.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting                                                             [ OK ]
alex@SMEGPREPGDB01:~$ sudo apt-get --purge remove apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
alex@SMEGPREPGDB01:~$ sudo apt-get --purge remove apache
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
alex@SMEGPREPGDB01:~$

```

---

### Post by gabisabobo on 2011-06-18
this way to remove apache2 completly 

1st use synaptic manager 
and than 
sudo apt-get autoremove apache2

---

### Post by lockit on 2011-06-19
> **gabisabobo said:**
> this way to remove apache2 completly 

1st use synaptic manager 
and than 
sudo apt-get autoremove apache2

Unfortunately on the server edition there is no graphical interface ... but you gave me a good idea...

I've use this command to search what there was installed: dpkg -l | grep apache2

And I deleted it almost one by one:
sudo apt-get autoremove libapache2-mod-php5
sudo apt-get autoremove libapache2-mod-wsgi
sudo apt-get autoremove libapache2-mod-python
sudo apt-get autoremove apache2-utils

Now apache is gone :D

---

### Post by lisati on 2011-06-19
Hmm, really old thread, things have moved on a bit since this thread was started. If you have aptitude installed, then this should do the trick for removing apache2:
```
sudo aptitude purge apache2
```
As for the downloading of PHP files, it is covered here:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

---

