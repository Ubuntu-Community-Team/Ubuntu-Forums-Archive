---
title: "mysql 5.1 broken"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-15
mysql is not working right I think it is because of amarok.
```

@ubuntu:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following partially installed packages will be configured:
  mysql-server-5.1
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up mysql-server-5.1 (5.1.30-2ubuntu3) ...
 * Stopping MySQL database server mysqld                                                                   [ OK ]
 * Starting MySQL database server mysqld                                                                   [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.1 (5.1.30-2ubuntu3) ...
 * Stopping MySQL database server mysqld                                                                   [ OK ]
 * Starting MySQL database server mysqld                                                                   [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

```

---

### Post by DougieFresh4U on 2009-01-15
> **LordVeovis said:**
> mysql is not working right I think it is because of amarok.
 I believe it is the other way around, amarok is broke because of 'mysql'. 
I had started a thread  yesterday morning concerning this ( then some one else started another thread) and had posted my terminal output.
I may be wrong?

---

### Post by LordVeovis on 2009-01-15
Is there any fix?

---

### Post by Vorian on 2009-01-15
Here is the issue.

Mysql versions are not co-installable.

At the moment, we have mysql 5.0 and mysql 5.1.  The only use for mysql 5.1 right now is for Amarok.

It is not necessary for mysql to 'start' for amarok to function properly.  Other KDE apps use mysql 5.0 (like Kmail).  So basically at this point, you have to choose to have Amarok, or Kmail and akonadi.

This is a known issue, and it is being worked on by the server team and kubuntu team.

---

### Post by LordVeovis on 2009-01-16
I am fine with only having only amarok, I use gnome, I just like amarok best as far as players go.  How would I get that to upgrade to 5.1 then?

---

### Post by tawmas on 2009-01-16
> **LordVeovis said:**
> I am fine with only having only amarok, I use gnome, I just like amarok best as far as players go.  How would I get that to upgrade to 5.1 then?

There was a thread a few days ago about an option that you need to delete from MySQL configuration file before 5.1 can start (it used to be valid for 5.0, but it is no longer valid for 5.1).

Let me dig for it, and I'll post a link for you.

---

### Post by tawmas on 2009-01-16
Got it! Check [this post]("http://ubuntuforums.org/showpost.php?p=6547238&postcount=5") and see if it helps you...

---

### Post by LordVeovis on 2009-01-30
Ha, nice.  This worked for me 2x.  The first time (a while back) it worked for me by commenting out the line mentioned.  The second time I had to follow the link and it said to do a ```
 sudo apt-get remove --purge mysql-server-5.1
sudo apt-get autoremove
sudo rm -rf /etc/mysql
sudo apt-get install mysql-server-5.1
```and that worked again as well.

---

