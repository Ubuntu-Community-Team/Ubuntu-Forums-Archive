---
title: "Uninstall vsftpd problem"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by gniss on 2010-02-18
I played with vsftpd and then used apt-get remove to uninstall it. Now, whenever I use apt-get I get an error as below. How do I go about figuring out what this message is about and how to get rid of it please.

```
hm@minerals:~$ sudo apt-get remove vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vsftpd
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 475kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 37489 files and directories currently installed.)
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by harmeet on 2010-02-19
Before you attempt to uninstall, make sure you don't have any ftp clients logged in, and then stop vsftpd by issuing this command -

```
sudo /etc/init.d/vsftpd stop
```

Then make sure there is no instance of vsftpd running by issuing this command -

```
ps -ef | grep vsftpd
```

---

### Post by chris_lukehart on 2010-02-20
First:

sudo /etc/init.d/vsftpd stop

Then use:

sudo aptitude remove vsftpd

INSTEAD OF:

sudo apt-get remove vsftpd

because:

aptitude removes it completely instead of apt-get

---

### Post by impresionist on 2010-10-03
For me it's not working, I tried in /etc/init.d/vsftpd stop, I get:

-bash: /etc/init.d/vsftpd: No such file or directory

And with ps -ef | grep vsftpd
I get:
root     17578 17380  0 18:25 pts/0    00:00:00 grep --color=auto vsftpd

I can't purge with aptitude, because I don't have it installed, and when I give apt-get install aptitude, I get the same error:
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
(Reading database ... 36705 files and directories currently installed.)
Removing vsftpd ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

:confused:
Any idea?

---

### Post by ByronJC on 2010-11-15
I'm having the same problem trying to switch to pure-ftpd and when trying to remove vsftpd no matter if I use apt-get, aptitude or dpkg I get the same error over and over.


root@voltagemedia:~# aptitude remove vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be REMOVED:
  libfile-copy-recursive-perl{u} update-inetd{u} vsftpd
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 688kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 41729 files and directories currently installed.)
Removing vsftpd ...
stop: Unknown instance:
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing update-inetd ...
Removing libfile-copy-recursive-perl ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

Current status: 1 broken [+1].
root@voltagemedia:~#

---

### Post by mrmcmoo on 2010-12-05
same problem - anyone finding a fix?

---

### Post by BigBotz on 2011-04-21
I was wondering if there was ever a fix to this problem because I am having it right now and cannot connect using FTP, I can only connect using ssh.
Thanks in advance!
Bigbotz

---

### Post by gaz90 on 2011-09-16
Deleted the "ftp" user in Users Settings - that cleared the error & removed the package.

---

### Post by oldos2er on 2011-09-16
Closed for necromancy.

---

