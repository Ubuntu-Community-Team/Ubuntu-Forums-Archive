---
title: "Cannot install upgrade remove Mysql 16.04 constant errors"
date: 2018-05-19
forum: Installation &amp; Upgrades
---

### Post by bulgin on 2018-05-19
Please point me to the proper sub forum if this is not the correct place to post for Mysql upgrade errors.

Whenever I attempt to do a distribution upgrade, it fails because Mysql throws errors which I believe makes it impossible to do a system-wide upgrade.

I am on Ubuntu 16.04.

Not matter what I do to remove, purge, delete, or otherwise get rid of a mysql system that is non-functioning and preventing me from upgrading the distribution, I constantly receive the following errors.  The following which seems to work for other people with this problem does not work for me:



```

sudo apt-get purge mysql*

sudo apt-get autoremove

sudo apt-get autoclean
  Then upgrade my distribution
  sudo apt-get dist-upgrade
  Then install MySQL 
  sudo apt-get install mysql-server


```

```

apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server-core-5.7
0 upgraded, 0 newly installed, 1 to remove and 131 not upgraded.
2 not fully installed or removed.
After this operation, 46.2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 287191 files and directories currently installed.)
Removing mysql-server-core-5.7 (5.7.22-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up mysql-common (5.7.22-0ubuntu0.16.04.1) ...
update-alternatives: error: alternative path /etc/mysql/my.cnf.fallback doesn't exist
dpkg: error processing package mysql-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mysql-client-5.7:
 mysql-client-5.7 depends on mysql-common (>= 5.5); however:
  Package mysql-common is not configured yet.

dpkg: error processing package mysql-client-5.7 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-common
 mysql-client-5.7
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

This is just insane as I cannot - under any circumstances or otherwise - get rid of this error.  Followed and attempted to do all the different commands listed elsewhere to purge, remove, delete, etc.  But I constantly receive this.

Should I just trash the system and start from scratch?

---

### Post by uRock on 2018-05-19
Try running the following in a terminal; ```
sudo apt install -f
```

---

### Post by bulgin on 2018-05-19
I ran all those other commands in a root terminal, but here they are again:
```

root@XXXX:/# apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 131 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-common (5.7.22-0ubuntu0.16.04.1) ...
update-alternatives: error: alternative path /etc/mysql/my.cnf.fallback doesn't exist
dpkg: error processing package mysql-common (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 mysql-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SeijiSensei on 2018-05-20
How about "sudo dpkg --configure -a" then "sudo apt -f install"? 

Did you run "sudo apt update" before any of this?   I don't see it in the transcript above.

---

### Post by bulgin on 2018-05-20
Thanks.

Always run sudo apt update before working on things.

This is the result of "sudo dpkg --configure -a" then "sudo apt -f install":
```

sudo dpkg --configure -a
Setting up mysql-common (5.7.22-0ubuntu0.16.04.1) ...
update-alternatives: error: alternative path /etc/mysql/my.cnf.fallback doesn't exist
dpkg: error processing package mysql-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libmysqlclient20:amd64:
 libmysqlclient20:amd64 depends on mysql-common (>= 5.5); however:
  Package mysql-common is not configured yet.

dpkg: error processing package libmysqlclient20:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmysqlclient20:i386:
 libmysqlclient20:i386 depends on mysql-common (>= 5.5); however:
  Package mysql-common is not configured yet.

dpkg: error processing package libmysqlclient20:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-common
 libmysqlclient20:amd64
 libmysqlclient20:i386

```

And then this is the result of "sudo apt -f install"
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-common (5.7.22-0ubuntu0.16.04.1) ...
update-alternatives: error: alternative path /etc/mysql/my.cnf.fallback doesn't exist
dpkg: error processing package mysql-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libmysqlclient20:amd64:
 libmysqlclient20:amd64 depends on mysql-common (>= 5.5); however:
  Package mysql-common is not configured yet.

dpkg: error processing package libmysqlclient20:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmysqlclient20:i386:
 libmysqlclient20:i386 depends on mysql-common (>= 5.5); however:
  Package mysql-common is not configured yet.

dpkg: error processing package libmysqlclient20:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
         Errors were encountered while processing:
 mysql-common
 libmysqlclient20:amd64
 libmysqlclient20:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SeijiSensei on 2018-05-20
I wonder if it's because of

```

 libmysqlclient20:amd64
 libmysqlclient20:i386

```

You have the same library in both architectures.  Maybe you should try purging the non-matching one, then try the fixes again.

---

### Post by bulgin on 2018-05-21
Sure enough it was the i386 conflict. 

Thanks for the help that solved it!

---

### Post by SeijiSensei on 2018-05-22
Wow, I didn't expect I'd guess the right answer!

---

