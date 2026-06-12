---
title: "Where is Apache?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by camroe on 2007-10-19
I'm trying to install apache2 and can't seem to do it! I'm running Feisty Faun 7.04. I give the command

sudo apt-get install apache2          and get the following 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
Need to get 38.7kB of archives.
After unpacking, 86.0kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main apache2 2.2.3-3.2ubuntu0.1 [38.7kB]
Fetched 38.7kB in 15s (2434B/s) 
Selecting previously deselected package apache2.
(Reading database ... 120945 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.3-3.2ubuntu0.1_all.deb) ...
Setting up apache2 (2.2.3-3.2ubuntu0.1) ...

cam@ubuntu-desktop:/home/cam#

There is no apache installed! I have searched for apachectl , any apache directory, anything and nothing. A friend of mine installed it and it installed it under /etc/apache2 but .. nothing.

So I remove it

sudo apt-get remove apache2                   and get the following 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2
0 upgraded, 0 newly installed, 1 to remove and 40 not upgraded.
Need to get 0B of archives.
After unpacking, 86.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120947 files and directories currently installed.)
Removing apache2 ...
cam@ubuntu-desktop:/home/cam#

I do this several times until i'm convinced that nothing happens. Any ideas?


Cheers

Cam

---

### Post by disasm on 2007-10-19
> **camroe said:**
> I'm trying to install apache2 and can't seem to do it! I'm running Feisty Faun 7.04. I give the command

sudo apt-get install apache2          and get the following 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
Need to get 38.7kB of archives.
After unpacking, 86.0kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main apache2 2.2.3-3.2ubuntu0.1 [38.7kB]
Fetched 38.7kB in 15s (2434B/s) 
Selecting previously deselected package apache2.
(Reading database ... 120945 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.3-3.2ubuntu0.1_all.deb) ...
Setting up apache2 (2.2.3-3.2ubuntu0.1) ...

cam@ubuntu-desktop:/home/cam#

There is no apache installed! I have searched for apachectl , any apache directory, anything and nothing. A friend of mine installed it and it installed it under /etc/apache2 but .. nothing.

So I remove it

sudo apt-get remove apache2                   and get the following 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2
0 upgraded, 0 newly installed, 1 to remove and 40 not upgraded.
Need to get 0B of archives.
After unpacking, 86.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120947 files and directories currently installed.)
Removing apache2 ...
cam@ubuntu-desktop:/home/cam#

I do this several times until i'm convinced that nothing happens. Any ideas?


Cheers

Cam

Try doing this:
dpkg --purge apache2 apache2-mpm-worker apache2-mpm-prefork apache2-mpm-event
apt-get clean
apt-get install apache2

Sam

---

### Post by camroe on 2007-10-20
No joy. I get all kinds of errors attempting to do this. 



root@ubunto-desktop:/etc# dpkg --purge apache2 apache2-mpm-worker apache2-mpm-prefork apache2-mpm-even
(Reading database ... 120947 files and directories currently installed.)
Removing apache2 ...
dpkg - warning: ignoring request to remove apache2-mpm-worker which isn't installed.
dpkg: dependency problems prevent removal of apache2-mpm-prefork:
 libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is to be removed.
  Package apache2-mpm-itk is not installed.
dpkg: error processing apache2-mpm-prefork (--purge):
 dependency problems - not removing
dpkg - warning: ignoring request to remove apache2-mpm-even which isn't installed.
Errors were encountered while processing:
 apache2-mpm-prefork
root@ubunto-desktop:/etc# 

Other idea's?  I think I'm going to try to build it from the source and see where that leads me. ... probably down the rabbit hole but .... ;) 

Any other ideas would be appreciated. ;)

---

### Post by disasm on 2007-10-20
try apt-get --purge remove libapache2-mod-php5 apache2

And then installing.

Sam

---

