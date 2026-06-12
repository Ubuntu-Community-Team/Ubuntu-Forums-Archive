---
title: "How to get mysql/mariadb to re-install over again so I can re-set root password"
date: 2019-07-31
forum: Installation &amp; Upgrades
---

### Post by pizzipie on 2019-07-31
Running Ubuntu Mate 18.04 
 
Messed up install of MariaDb didn't get setting of root pw correct. 
 
Tried to reset root password by using procedure on internet for lost root pw. 
 
Got nowhere except errors. 
 
How can I purge everything so a restart of mariadb and/or mysql will go through the routine to set root password. 
 
I tried using Synaptic to completely uninstall these apps. Doesn't work. 
 
Thanks for help 
 
R

---

### Post by TheFu on 2019-08-01
```
sudo apt purge {package name}
```
That will remove all the files included in the package.
It will not remove files NOT included in the package like any personal settings in your HOME or any data files.  Those must be manually removed.

---

### Post by pizzipie on 2019-08-02
Hi,
Thanks for your reply. 

I have tried **apt purge **but on re-install you do not get to set your root password.
I got looking around and found the following directories still left on my machine. So much for apt purge.

============================================
**MySql Directories Left**

/etc/mysql
/var/log/mysql
/var/lib/mysql
/var/lib/mysql/mysql
**/usr/share/php7.2-mysql/mysql**
/usr/share/mysql
/run/mysqld

----------------------------------------------------

**MariaDb Directories left**

/etc/mysql/mariadb.conf.d
/etc/systemd/system/mariadb.service.d
=============================================
 
My inclination is to remove them all except ** /usr/share/php7.2-mysql/mysql **since it appears to effect PHP.

I **REALLY** want to avoid having to re-install Ubuntu 18.04 again.

I have backed up all my Database files. I also have removed PhpMyAdmin since it has db files associated with it.

Any thoughts? 

R

---

### Post by TheFu on 2019-08-02
The DB password is stored inside the DB files.

I think you misunderstood what I wrote.  If they aren't files included in the installer package, then they aren't removed.  Directories are left. From the apt manpage:
```
           Removing a package removes all packaged data, but leaves usually
           small (modified) user configuration files behind, in case the
           remove was an accident. Just issuing an installation request for
           the accidentally removed package will restore its function as
           before in that case. [B]On the other hand you can get rid of these
           leftovers by calling purge even on already removed packages.[/B] Note
           that this does not affect any data or configuration stored in your
           home directory.

```

The manpage for apt-get says:```

       purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).
```
If you are running servers, learning to use the manpages is mandatory.  That's the best information available for the versions of programs on your system.

---

### Post by pizzipie on 2019-08-02
So should I get rid of the mysql database in order to get rid of user root with the lost password

---

### Post by pizzipie on 2019-08-03
Well even though I was disappointed that no one knew the answer to this or just didn't care and after looking around the internet for a number of hours I found an answer; I found the site below because of the 1698 error I got trying to make things work

**[https://superuser.com/questions/957708/mysql-mariadb-error-1698-28000-access-denied-for-user-rootlocalhost](https://superuser.com/questions/957708/mysql-mariadb-error-1698-28000-access-denied-for-user-rootlocalhost)**

Basically I renamed /var/lib/mysql to /var/lib/oldmysql.  I think that since the old mysql table data was not accessible any more the install created another /var/lib/mysql directory with a new user  table with only a root user.  I used  sudo mysql  to get into mysql and start the process.

What I found in the site above is that you can add a root password, delete the plugin data (so field plugin is blank) and you can now start mysql like this
 mysql -u root -p newPW and it will start.

I realize that this article has a lot of technical stuff about the plugins and authentications without using a password and so on. That is all way over my head.

So thank you who replied and I hope this info will prevent someone else many hours of frustration,

Thanks, R

---

