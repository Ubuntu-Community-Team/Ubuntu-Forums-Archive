---
title: "newbie/ installing mysql-server-5.0 error"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by pius1225 on 2007-11-09
hi,

ive tried to install mysql-server-5.0 by running "apt-get install mysql-server-5.0" and i get the error then it stop.

Errors were encountered while processing:
 at
 ubuntu-standard
E: Sub-process /usr/bin/dpkg returned an error code (1)

any idea about this? would really appreciate any information.

Regards,
Pius

---

### Post by maxxfell on 2007-11-11
This is no help to you, but I'm having the same problem.

"mysql" was failing on boot.  When I removed the package and tried to reinstall, this was the output from "sudo aptitude install mysql-server-5.0"


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  mysql-server-5.0 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.8MB of archives. After unpacking 84.5MB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 196124 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3_i386.deb) ...
Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by maxxfell on 2007-11-11
Posting again because I got mysql working, so this might help you.

**CAVEAT: This worked, in that I did get mysql running.  But I'm not really well informed about how this stuff works.  In particular, I'm not sure that my back-up and restore procedure is right.  It looks like it worked, but it could still turn out not to have.**

What I had to do was completely remove mysql and all its data.  When I reinstalled it, it started up with no problem.  This is what I did:

1. back up the mysql data, which is in /var/lib/mysql

```
sudo cp -r /var/lib/mysql /var/lib/mysql.b
```

2. purge mysql-server.  I did this by using synaptic and selecting "completely remove".
But it would be quicker to use the command line:

```
sudo aptitude purge mysql-server
```

3. When a message comes up asking if you want to remove all database files, agree to do so.

4. Once the removal of mysql-server-5.0 is complete, you can reinstall it, using synaptic or aptitude or whatever.

```
sudo aptitude install mysql-server
```

5. Then restore the data that was backed up in the beginning

```
sudo cp -r /var/lib/mysql.b /var/lib/mysql
```

6. Stop the mysql daemon and restart it, just to check that it's still working.

```
sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start
```

That's it.  But it's still a mystery to me why I should have had to do this to get mysql working.

Hope this helps anyway.
M

---

