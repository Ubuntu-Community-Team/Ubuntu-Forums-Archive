---
title: "How to completely reinstall Apache2?"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Xteven on 2008-09-07
So I had Apache2 running perfectly fine on my server. I then tried to install MediaWiki but that got me into some totally weird and unnecessary problems. So for some strange reason I had the bad idea to remove everything including Apache2... now I can't even get that to work properly.

I stopped apache2, killed all its processes and then performed..

$ sudo apt-get remove --purge apache2
$ sudo apt-get clean
$ sudo apt-get purge
$ sudo apt-get autoremove

Which produced the following output:

```

account@server:~$ sudo apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
Need to get 0B of archives.
After unpacking 94.2kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 45849 files and directories currently installed.)
Removing apache2 ...

account@server:~$ sudo apt-get clean

account@server:~$ sudo apt-get purge
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

account@server:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```

Then I tried to get apache2 back like so:

```

account@server:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 42.2kB of archives.
After unpacking 94.2kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy-updates/main apache2 2.2.4-3ubuntu0.1 [42.2kB]
Fetched 42.2kB in 0s (63.6kB/s)
Selecting previously deselected package apache2.
(Reading database ... 45845 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.4-3ubuntu0.1_all.deb) ...
Setting up apache2 (2.2.4-3ubuntu0.1) ...
```

It seems like apache2 was installed.. (all 42.2kB of it... why so small???) But no directories exist and the init.d file isn't there:

```

account@server:/etc$ cd /etc/apache2
-bash: cd: /etc/apache2: No such file or directory

account@server:/etc/init.d$ ls -al | grep apache
account@server:/etc/init.d$
```

How can I completely remove then reinstall the apache2 server as it comes with Ubuntu's repositories...? 

I am running Ubuntu Server 7.10:

account@server:~$ uname -a
Linux server 2.6.22-15-server #1 SMP Wed Aug 20 16:11:14 UTC 2008 x86_64 GNU/Linux

---

### Post by Xteven on 2008-09-10
Bump. 

I really don't think this requires that I reinstall Ubuntu, that would be horribly inefficient.

---

### Post by bikeboy on 2008-09-10
The plain apache2 package isn't really the program, it's a metapackage iirc.

Try 'sudo apt-get autoremove' after removing the apache2 package. That should find all the stuff associated with apache2 that is no longer needed due to dependencies.

---

### Post by Xteven on 2008-09-10
Okay just got the answer off IRC:

Last time I was just running

```
sudo apt-get --purge remove apache2 apache2.2-common
```

and it only remove 94kb of stuff. For some odd reason if I just try:

```
sudo apt-get --purge remove apache2.2-common
```

it removes 32 megs of stuff...including some of which are these:

apache2* apache2-mpm-prefork* apache2.2-common* libapache2-mod-php5* php5* 

So I then just ran this:

```
sudo apt-get install apache2 apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5
```

Everything back to normal for me now.

---

