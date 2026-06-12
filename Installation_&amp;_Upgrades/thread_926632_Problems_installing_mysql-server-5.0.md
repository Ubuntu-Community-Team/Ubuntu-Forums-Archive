---
title: "Problems installing mysql-server-5.0"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by joonty on 2008-09-22
Hi everyone,

I'm relatively new to linux, I know commands but have no understanding of the inner workings. I'm trying to set up apache, mysql and php on my computer to run a localhost for web development. I happily sailed through the apache config and installation, but when it came to mysql I had a nightmare trying to install it from source. So eventually I realised I could "apt-get mysql-server-5.0", which was much easier.

Except...

It fails to start. I've been Googling my head off trying to find other people with the same problem, which I have. But none of the solutions that they had worked for me. Here's what happens when I install it:

```

$ sudo apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  libhtml-template-perl mailx
The following NEW packages will be installed
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/28.0MB of archives.
After this operation, 89.2MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 97284 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.1_amd64.deb) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                [ OK ] 
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone help me?

Many thanks, Joonty

---

### Post by gervin23 on 2008-10-14
I too am having problems with MySQL. 

I believe the deb is broken in a couple areas in particular with the apparmor profile. I was able to get it running by purging the server install ('sudo apt-get purge mysql-server-5.0') and reinstalling. It will fail to start and give the following error:

```
Reloading AppArmor profiles Error: #include <abstractions/mysql> not found at line 9 in /etc/apparmor.d/usr.sbin.mysqld
```

I tried disabling the profile (placing usr.sbin.mysqld in /etc/apparmor.d/disable) but that doesn't do what I expected so I just deleted /etc/apparmor.d/usr.sbin.mysqld and restarted mysql. Unfortunately, many settings like the master password didn't complete and I'm still figuring out what's missing but this should at least get mysqld up and running.

Andrew

---

